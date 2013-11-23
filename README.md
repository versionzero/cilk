Cilk
===

This directory contains Cilk, a language for multithreaded parallel
programming based on ANSI C.  Cilk is designed for general-purpose
parallel programming, but it is especially effective for exploiting
dynamic, highly asynchronous parallelism.  This release contains the
Cilk compiler, the Cilk runtime system, and example programs.

This release of Cilk is targeted at the computing community at large,
and not only at parallel-computing specialists.  We tried to make Cilk
easy to install and to use.  If you know the C language, you should be
able to write simple parallel Cilk programs quickly.

Cilk has been developed since 1994 at the MIT Laboratory for Computer
Science by Prof. Charles E. Leiserson and his group.  Besides being
used for research and teaching, Cilk was the system used to code the
three world-class chess programs *Tech, *Socrates, and Cilkchess.
Over the years, implementations of Cilk have run on computers ranging
from networks of Linux laptops to an 1824-nodes Intel Paragon.

The current Cilk-5.4 release runs on symmetric multiprocessor (SMP)
machines that support Posix threads, GNU make, and gcc.  Cilk-5.4 was
developed and tested mainly on GNU/Linux, but porting Cilk to other
Unix systems where the GNU compilation tools are available should be
quite easy.  You can also run Cilk-5.4 on uniprocessor machines.  This
configuration is useful for program development and debugging, even
though you will not get any parallel speedup.

The doc/ directory contains the Cilk manual.  The cilk2c/ and runtime/
directories contain the Cilk compiler and runtime system,
respectively.  The examples/ directory contains example programs.

System Requirements
-------------------

In order to run Cilk, you need the following packages:

* A recent version of gcc.  Cilk-5.4 was tested with `gcc-2.95`,
  `gcc-2.8.x`, `gcc-4.7.3` and `egcs-1.1`.  `gcc-2.7.x` does not work.
* An implementation of POSIX threads.  Cilk-5.4 was tested with
  LinuxThreads (glibc-2.1) on linux/386 and linux/powerpc, Solaris
  2.6, and IRIX 6.5.
* A recent version of GNU `make`.  GNU `make `3.81 is known to work.
* The GNU linker is desirable (although not required).  Cilk can be
  compiled as a shared libraries if the GNU linker is available.

The following processor families are supported:

* Intel IA-32.  (tested on Pentium, Pentium II, and Pentium III)
* SPARC.  (tested on UltraSPARC-I)
* PowerPC. (tested on PowerPC 750 aka G3)
* Alpha.   (tested on 21264)
* MIPS.    (tested on R10000)
* Intel IA-64. 
* ARM.     (test on Cortex-A9, i.e. ODROID-U2)

Porting to other architectures requires a few lines of assembly code
to implement memory barriers and mutual-exclusion locks.

Building From Scratch
---------------------

If you choose to build Cilk straight out of the subversion repository,
you will find that certain files are not present.  These files include

    aclocal.m4
    configure.in
    configure

... and many Makefile.in files in various directories.  To build those
files, you will need `aclocal`, `automake`, and `autoconf`. I made
this work on a Debian "wheezy".  I made it work with `automake-1.11.6`
and `autoconf-2.69`.

You do this:

    aclocal
    automake
    autoconf
    ./configure CFLAGS="-D_XOPEN_SOURCE=600 -D_POSIX_C_SOURCE=200809L"
    make

If you are compiling on a modern Linux, the above `CFLAGS` is *required*.

Copyright
---------

Copyright (c) 2000 Massachusetts Institute of Technology

Copyright (c) 2000 Matteo Frigo

Portions of cilk2c Copyright (c) 1989, 1990 James A. Roskind 


License
-------

Cilk is distributed under the terms of the GNU General Public License.
See file COPYING for details.


Contacts
--------

For new releases, documentation, and up-to-date information, please
refer to: http://supertech.lcs.mit.edu/cilk

Cilk is currently maintained by Matteo Frigo <athena@fftw.org>.
Please send email to cilk-support@lists.sourceforge.net for
suggestions, bug reports, and questions about Cilk.
