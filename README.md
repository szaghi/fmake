fmake
=====

_fmake_ is a small script for the easy creation of makefile for Fortran (standard 90 or higher) projects. The aim is to easily create the compiling rules with the correct hierarchy for inter-dependent modules, a task that could be very boring for big project with many source files.

The created makefile can produce colorful std-output and save compilation errors and warnings on separate log files.

Usage
-----

### help

_fmake_ has a simple help documentation. Run:

> fmake -h

and the help printed is as following:

      fmake 0.1: a small script for the easy creation of makefile for Fortran (standard 90 or higher) projects
      the aim is to easily create the compiling rules with the correct hierarchy for inter-dependent modules
      Usage: fmake [options [args]]
      Options:
        -h
          print this help message
        -s [dir]
          dir = directory containing source files .[fF][90,95,03,08,2k], default './src/'
        -m [makefile]
          makefile = file name of the output makefile, default 'makefile'
        -header or -hd [header]
          header = file containing the 'user defined header' of makefile, it is not used by default
          Note:
               if no header file is used a very basic header of the makefile is automatically created by fmake
               and the user must check the makefile before use it
        -fc [fortran_compiler]
          fortran_compiler = name of Fortran compiler, default 'gfortran'
        -dobj [dir_obj]
          dir_obj = compiled objects directory name, default './obj/'
        -dmod [dir_mod]
          dir_mod = module interfaces directory name, default './mod/'
        -dexe [dir_exe]
          dir_exe = executable programs directory name, default './'
        -optc ['compiling_options']
          compiling_options = compiling options, default '-c -J$(DMOD)'
        -optl ['linking_options']
          linking_options = linking options, default ''
        -libs ['libraries_list']
          libraries_list = external libraries to be linked, default ''
        -simple
          produce a simple makefile without colorful output and compilation errors/warnings log files
      Note:
           The hierarchy of compiling rules is made up without the intrinsic modules, namely the 'OMP_LIB' and 'MPI' modules.

### makefile creation

Let us assume your source files are in "sources" directory. A colorful makefile without customized header can be created by

> fmake -s sources/

A very simple makefile without colourful std-output and log files cab be created by

> fmake -s sources/ -simple

If you want a more complicated makefile with customized header you can use your own header file:

> fmake -s sources/ -header YourHeaderFile

Note that by default a file named _makefile_ is created. Its name can be changed by the CLI switch "-m YourCustomName"

ToDo
----

* Recursive search for source files;
* GUI.

Copyrights
----------

_fmake_ is an open source script, it is distributed under the [GPL v3](http://www.gnu.org/licenses/gpl-3.0.html). Anyone is interest to use, to develop or to contribute to _fmake_ is welcome.
