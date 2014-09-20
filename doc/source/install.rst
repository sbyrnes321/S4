Download & Installation
=======================

There are two choices for downloading |S4|: downloading a binary package from below, or cloning the GitHub respository and building from source.
The latter is the preferred method for obtaining the latest features and bug fixes.

Binary packages
---------------

The binary packages do not contain the examples and documentation, and are compiled with the bare minimum of features.
You need to download that separately.

* Version 1.1.1

  * `Windows (32-bit) EXE <files/S4-1.1.1-win32.7z>`_ (Lua frontend)
  * `Mac OS X (compiled on 10.8.5) <files/S4-1.1.1-osx.gz>`_ (Lua frontend)
  * `Examples and documentation <files/S4-1.1.1-doc.tar.gz>`_

* Version 1.0 (not recommended)

  * `Source with documentation and examples <files/S4-1.0.0.tar.gz>`_
  * `Windows EXE <files/S4-1.0.0-bin-win32.zip>`_
  * `Mac OS X 10.6.8 <files/S4-1.0.0-bin-osx.tar.gz>`_
  
GitHub repository
-----------------

The source code is located at this `GitHub repository <https://github.com/victorliu/S4>`_.
You can clone it with the command::

	git clone https://github.com/victorliu/S4.git

Compiling from source
---------------------

Dependencies
^^^^^^^^^^^^

Before compiling, there are a number of packages that are recommended.
None of these is required except for either Lua or Python.

* `Lua <http://www.lua.org>`_ 5.2.x - This is required for the Lua frontend.
  Either this or Python is required.
  On Ubuntu or Debian, the repository packages are called ``liblua5.2``
  and ``liblua5.2-dev``.
* `Python <http://python.org>`_ 2.x or 3.x - This is required to build |S4| as a Python extension.
  Either this or Lua is required.
  On Ubuntu or Debian, the repository package is called ``python-dev`` or ``python3-dev``.
* BLAS and Lapack implementation - Optional, but highly recommended. It is suggested that `OpenBLAS <http://www.openblas.net/>`_ be used.
* `FFTW3 <http://fftw.org>`_ - Optional, provides a 2-3x speedup in FFT computations.
  On Ubuntu or Debian, the repository package is called ``libfftw3-dev``.
* `CHOLMOD <http://www.cise.ufl.edu/research/sparse/cholmod/>`_ - Optional, provides a speedup in certain FMM formulations.
  On Ubuntu or Debian, install the repository package is called ``libsuitesparse-dev``.
* POSIX Threads - Optional, typically provided by the compiler. Allows multi-threading support on shared-memory machines.
* MPI - Optional, provides support for parallel computing on distributed-memory machines.

Compilation
^^^^^^^^^^^^^^^^^^^^^^^^

# Edit Makefile.custom and set the library flags for all the dependencies that can be provided.
# Run::

	make

# Next, build either the Lua frontend::

	make S4lua

  or the Python extension::

	make S4_pyext

# The resulting Lua binary is just called ``S4``. The Python shared
  object is ``build/lib.*/S4.so``. To use the Python API, run
  ``python setup.py install``, and now you can ``import S4`` in any
  python script.

# If you change any aspect of the compilation, run ``make clean`` before
  re-running ``make``.
.. |S4| replace:: S\ :sup:`4`
