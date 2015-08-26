PGI Compilers
=============
The PGI Compiler suite offers C,C++ and Fortran Compilers. For full details of the features of this compiler suite, see PGI's website at http://www.pgroup.com/products/pgiworkstation.htm

Making the PGI Compilers available
----------------------------------

After connecting to iceberg (see :ref:`ssh`),  start an interactive session with the :code:`qsh` or :code:`qrsh` command. To make one of the versions of the PGI Compiler Suite available, run one of the following module commands ::

    module load compilers/pgi/15.7
    module load compilers/pgi/14.4
    module load compilers/pgi/13.1

Compilation examples
--------------------
**C**

To compile the C hello world example into an executable called ``hello`` using the PGI C compiler ::

    pgcc hello.c -o hello

**C++**

To compile the C++ hello world example into an executable called ``hello`` using the PGI C++ compiler ::

      pgc++ hello.cpp -o hello

**Fortran**

To compile the Fortran hello world example into an executable called ``hello`` using the PGI Fortran compiler ::

      pgf90 hello.f90 -o hello

Additional resources
--------------------

* :ref:`Using the PGI Compiler with GPUs on Iceberg <PGI_Compiler_GPU>`

Installation Notes
------------------
*Version 15.7*

The installer is interactive. Most of the questions are obvious.
Here is how I answered the rest

Installation type ::

  A network installation will save disk space by having only one copy of the
  compilers and most of the libraries for all compilers on the network, and
  the main installation needs to be done once for all systems on the network.

  1  Single system install
  2  Network install

  Please choose install option: 1

Path ::

  Please specify the directory path under which the software will be installed.
  The default directory is /opt/pgi, but you may install anywhere you wish,
  assuming you have permission to do so.

  Installation directory? [/opt/pgi] /usr/local/packages6/compilers/pgi

CUDA and AMD components ::

  Install CUDA Toolkit Components? (y/n) y
  Install AMD software components? (y/n) y

AMCL version ::

  This PGI version links with ACML 5.3.0 by default.  Also available:
    (1) ACML 5.3.0
    (2) ACML 5.3.0 using FMA4
  Enter another value to override the default (1)
  1

Other questions ::

  Install JAVA JRE [yes] yes
  Install OpenACC Unified Memory Evaluation package? (y/n) n
  Do you wish to update/create links in the 2015 directory? (y/n) y
  Do you wish to install MPICH? (y/n) y
  Do you wish to generate license keys? (y/n) n
  Do you want the files in the install directory to be read-only? (y/n) n

The license file is on the system at ``/usr/local/packages6/compilers/pgi/license.dat`` and is a 5 seat network license. Licenses are only used at compile time.

Modulefile
----------
The PGI compiler installer creates a suitable modulefile that's configured to our system. It puts it at ``/usr/local/packages6/compilers/pgi/modulefiles/pgi64/15.7`` so all that is required is to copy this to where we keep modules at ``/usr/local/modulefiles/compilers/pgi/15.7``