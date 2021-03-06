.. index:: Installation


============
Installation
============

Requirements
------------

SlimerJS runs on any platform on which Firefox or XulRunner is available: Linux (32bits and 64bits),
Windows, MacOs X. XulRunner is the core of Firefox without its user interface.

On windows, you should open a terminal. You can use the classical cmd.exe, or the recent PowerShell.exe.
You can also install `Cygwin <http://www.cygwin.com/>`_ and use its terminal.

You cannot use the MingW32 environment on Windows because there are some issues with
(no output in the console, and it lacks on some commands like mktemp).

Installation of SlimerJS
------------------------

.. index::  linux, package

To install SlimerJS, you need to download its package. It is available in two editions:


- The **Standalone Edition**: this is a zip/gz package containing
  SlimerJS **and** XulRunner. There is a package for each operating system.
  Download it, extract it. *Everything is here*. You're ready to use SlimerJS.
  Go to the :ref:`Lauching SlimerJS <launch>` section.
- The **Lightweight Edition**: this is a zip package containing
  only SlimerJS and it targets all operating system. You have to install Firefox or XulRunner
  separately (version 22 or more) and probably you'll need to
  :ref:`set an environment variable <setup>`.
  This package can be downloaded from slimerjs.org. Or it can be installed from a
  repository like the Arch Linux's repository or Homebrew.

See the `download page <http://slimerjs.org/download.html>`_ to know the places from
where you can retrieve SlimerJS.
  

.. index:: SLIMERJSLAUNCHER

.. _setup:

Configuring SlimerJS
--------------------

During its launch, SlimerJS tries to discover itself the path of Firefox or
XulRunner. This is not a problem for the *Standalone edition* or linux packages.

In case it fails (this could be the case for the *lightweight edition*), or if you want
to launch SlimerJS with a specific version of Firefox, you should create an environment
variable containing the path of the Firefox/XulRunner binary. To create this environment
variable from a command line:

- On linux:
   .. code-block:: bash

      export SLIMERJSLAUNCHER=/usr/bin/firefox

- on Windows
   .. code-block:: text

      SET SLIMERJSLAUNCHER="c:\Program Files\Mozilla Firefox\firefox.exe

- On windows with cygwin
   .. code-block:: bash

      export SLIMERJSLAUNCHER="/cygdrive/c/program files/mozilla firefox/firefox.exe"

- On MacOS
   .. code-block:: bash

      export SLIMERJSLAUNCHER=/Applications/Firefox.app/Contents/MacOS/firefox


You can of course set this variable in your .bashrc, .profile or in the computer
properties on Windows.

.. _launch:

Launching SlimerJS
------------------

From a command line, call the `slimerjs` executable (or ``slimerjs.bat`` for Windows)
with the path of a javascript file.

.. code-block:: bash

    /somewhere/slimerjs-1.2.3/slimerjs myscript.js
    # or if SlimerJS is in your $PATH:
    slimerjs myscript.js

On Windows:

.. code-block:: text

    c:\somewhere\slimerjs-1.2.3\slimerjs.bat myscript.js

The js script should contain your instructions to manipulate a web page...

You can indicate several options on the command line. See the "configuration" chapter.

Having a headless SlimerJS
--------------------------

There is a tool called xvfb, available on Linux and MacOS. It allows to launch
any "graphical" programs without the need of an X-Windows environment. Windows of
the application won't be shown and will be drawn only in memory.

Install it from your prefered repository (``sudo apt-get install xvfb`` with debian/ubuntu).

Then launch SlimerJS like this:

.. code-block:: bash

    xvfb-run ./slimerjs myscript.js

You won't see any windows. If you have any problems with xvfb, see its
documentation.
