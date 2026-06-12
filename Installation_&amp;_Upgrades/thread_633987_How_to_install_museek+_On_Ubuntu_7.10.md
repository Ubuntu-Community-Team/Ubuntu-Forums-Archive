---
title: "How to install museek+ On Ubuntu 7.10?"
date: 2007-12-07
forum: Installation &amp; Upgrades
---

### Post by Ilias83 on 2007-12-07
Hello there.
I've installed Ubuntu 7.10 yesterday.
This is the first time I'm using Linux.
I like them but I have problems installing Programs and Drivers.
I need help installing museek+.
I downloaded a file named museek+-0.1.13.tar.gz
I extract it on a folder named museek+-0.1.13 (don't laugh but I was trying to find out how for about 20 minutes)
typing
tar -xf museek+-0.1.13.tar.gz
from terminal.
Now I don't know what to do...
Any help?

---

### Post by logos34 on 2007-12-07
Check the README and INSTRUCTIONS files that you have the reqs/dependencies

then

$ cd museek+-0.1.13
$ cmake 
$ make 
$ sudo make install

---

### Post by Ilias83 on 2007-12-07
I tryied these steps:

ilias@ilias-desktop:~/Programs/museek+-0.1.13$ cmake
The program 'cmake' is currently not installed.  You can install it by typing:
sudo apt-get install cmake
bash: cmake: command not found
ilias@ilias-desktop:~/Programs/museek+-0.1.13$ sudo apt-get install cmake
[sudo] password for ilias:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  cmake
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 5017kB of archives.
After unpacking 12.7MB of additional disk space will be used.
Get:1 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) gutsy/main cmake 2.4.7-1 [5017kB]
Fetched 5017kB in 23s (211kB/s)                                                
Selecting previously deselected package cmake.
(Reading database ... 101224 files and directories currently installed.)
Unpacking cmake (from .../cmake_2.4.7-1_amd64.deb) ...
Setting up cmake (2.4.7-1) ...

ilias@ilias-desktop:~/Programs/museek+-0.1.13$ sudo apt-get install make
Reading package lists... Done
Building dependency tree       
Reading state information... Done
make is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Whatever I try fails...

---

### Post by logos34 on 2007-12-07
> ...
Get:1 [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) gutsy/main cmake 2.4.7-1 [5017kB]
Fetched 5017kB in 23s (211kB/s)
Selecting previously deselected package cmake.
(Reading database ... 101224 files and directories currently installed.)
Unpacking cmake (from .../cmake_2.4.7-1_amd64.deb) ...
Setting up cmake (2.4.7-1) ...

ilias@ilias-desktop:~/Programs/museek+-0.1.13$ [COLOR="Red"]sudo apt-get install make[/COLOR]

no, it just installed.  Now do 'cmake' again

but before you do that get build-essential if you don't have it already:

sudo apt-get install build-essential

---

### Post by Ilias83 on 2007-12-07
ilias@ilias-desktop:~/Programs/museek+-0.1.13$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ilias@ilias-desktop:~/Programs/museek+-0.1.13$ cmake
cmake version 2.4-patch 7
Usage

  cmake [options] <path-to-source>
  cmake [options] <path-to-existing-build>

Command-Line Options
  -C <initial-cache>          = Pre-load a script to populate the cache.
  -D <var>:<type>=<value>     = Create a cmake cache entry.
  -G <generator-name>         = Specify a makefile generator.
  -E                          = CMake command mode.
  -i                          = Run in wizard mode.
  -L[A][H]                    = List non-advanced cached variables.
  -N                          = View mode only.
  -P <file>                   = Process script mode.
  --graphviz=[file]           = Generate graphviz of dependencies.
  --debug-trycompile          = Do not delete the try compile directories..
  --debug-output              = Put cmake in a debug mode.
  --help-command cmd [file]   = Print help for a single command and exit.
  --help-command-list [file]  = List available listfile commands and exit.
  --help-module module [file] = Print help for a single module and exit.
  --help-module-list [file]   = List available modules and exit.
  --copyright [file]          = Print the CMake copyright and exit.
  --help                      = Print usage information and exit.
  --help-full [file]          = Print full help and exit.
  --help-html [file]          = Print full help in HTML format.
  --help-man [file]           = Print a UNIX man page and exit.
  --version [file]            = Show program name/version banner and exit.

Generators

The following generators are available on this platform:
  KDevelop3                   = Generates KDevelop 3 project files.
  Unix Makefiles              = Generates standard UNIX makefiles.

NOTE

CMake no longer configures a project when run with no arguments.  In order to
configure the project in the current directory, run

  cmake .

ilias@ilias-desktop:~/Programs/museek+-0.1.13$ 

As I can see I already had build-essential.

---

### Post by Ilias83 on 2007-12-08
Sorry I'm stuck again.
What's the next step?

---

### Post by logos34 on 2007-12-08
turns out this is one complicated program to build from source...is there any reason you're not installing the .debs in the repos?  I just checked and they're all listed

> $ apt-cache search museek
mucous - Python/curses client for museekd
museekd - Client for the SoulSeek peer-to-peer network (server daemon)
museekd-tools - Tools to manage a museekd daemon
museeq - Qt client for museekd
museeq-locales - Translations for museeq
musetup-gtk - Gtk based museekd configuration utility
python-museek - Python bindings for museek+

---

### Post by Ilias83 on 2007-12-09
You're absolutely right...!!!
They are listed...
I just thought they were not..
Thanks for your help...:D

---

### Post by revolutionaction on 2008-02-11
so Ilias83, I'm wondering if you got museek+ up and running? I've gotta try installing it later today.

---

### Post by Ilias83 on 2008-06-02
I finally installed museek+.
From Applications->Add/Remove... just search "museek" with option show "all available application" in the drop down menu.
You'll find it there.
There is also a program called Nicotine-Plus.
Try it.

---

