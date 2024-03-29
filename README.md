`assistant-scheduler` is a small tool for
scheduling teaching assistants in exercise groups.
It was originally developed for teachers of programming courses
at the CS department of Aalto University.
These courses can have roughly twenty teaching assistants and
exercise session groups.
As the assistants are students, they have other duties as well and
can thus only teach in some of the exercise groups.
Furthermore, some groups are required to have more assistants than others.
As finding an optimal scheduling under such constraints can be hard to do by hand, an automated tool was required and developed.

# Installation

The tool requires the [Python](https://www.python.org/) programming language,
version 3.6 or higher,
and uses the [Clingo](https://github.com/potassco/clingo) answer set solver tool under the hood.

One can use `pip` to install the tool directly from GitHub:
```
python3 -m pip install git+https://github.com/tjunttila/assistant-scheduler.git
```
See the [PyPA Installing Packages tutorial](https://packaging.python.org/tutorials/installing-packages/) for information on installing Python packages and on Python virtual environments.
For instance, on Linux machines one can create a Python virtual environment and
install the tool in it as follows:
```
python3 -m venv scheduler-venv
source scheduler-venv/bin/activate
pip install git+https://github.com/tjunttila/assistant-scheduler.git
```

# Usage

In the simplest case,
```
assistant-scheduler config_file
```
All the options can be printed with `assistant-scheduler --help`.

The configuration file describes the exercise groups and assistants.
It can be either in the [JSON](https://tools.ietf.org/html/rfc8259) or [YAML](https://yaml.org/) formats.
Please see the file [sample-1.yaml](sample-1.yaml) file for a commented YAML example,
and [sample-1.json](sample-1.json) for its JSON counterpart.
The file [sample-2.json](sample-2.json) contains a more constrained configuration example in which not all the requirements can be fulfilled.

Observe that, in addition to the "push enter and accept the produced result" mode,
the tool can also be used in a "possibility exploration" mode.
For instance, if an assistant wants to have all his/her groups within a day,
then one can modify the configuration file so that his/her groups are
only allowed on Tuesday, for instance,
and then run the tool to see whether the rest of the assistants
can still be scheduled in a satisfactory manner.

# License

The `assistant-scheduler` tool is released under the [MIT License](LICENSE).
