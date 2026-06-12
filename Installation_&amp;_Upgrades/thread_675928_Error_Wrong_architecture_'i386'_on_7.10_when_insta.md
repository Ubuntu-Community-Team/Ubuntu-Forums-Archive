---
title: "Error: Wrong architecture 'i386' on 7.10 when installing linux mce"
date: 2008-01-23
forum: Installation &amp; Upgrades
---

### Post by Josh.Bolger on 2008-01-23
Hi,

I am fairly new to this (I have just converted from windows) so let me apologise from the outset.

I am running an x64 amd chip and I have installed ubuntu 7.10 and vmware (was that a learning curve).

I am now trying to install linux mce from discs (not the dvd) and when i double click on the zip file the package install comes up with the following - error: wrong architecture 'i386'

Could somebody perhaps please step out how i fix this in relatively simple terms please?

Thanks

---

### Post by PmDematagoda on 2008-01-23
If you are running Ubuntu 64 bit, then you could install 32 bit packages by using:-
```
sudo dpkg -i --force-architecture nameofpackage.deb
```

---

### Post by Josh.Bolger on 2008-01-23
Thanks for that, I tried it and got
dpkg: status database area is locked by another process

do I need to enter the location of that package (its running off the cd)

---

### Post by PmDematagoda on 2008-01-23
Are you running any other package managers such as Synaptic or Adept? If so, then you should close them before executing the command.

---

### Post by Josh.Bolger on 2008-01-24
I made sure i turned off all the update packages and I did as follows:

josh@media-server:~$ sudo dpkg - --force-architecture mce-installer_2.0.1-1_i386.deb
[sudo] password for josh:
dpkg: need an action option

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
josh@media-server:~$ dpkg-deb --help
Usage: dpkg-deb [<option> ...] <command>

Commands:
  -b|--build <directory> [<deb>]   Build an archive.
  -c|--contents <deb>              List contents.
  -I|--info <deb> [<cfile> ...]    Show info to stdout.
  -W|--show <deb>                  Show information on package(s)
  -f|--field <deb> [<cfield> ...]  Show field(s) to stdout.
  -e|--control <deb> [<directory>] Extract control info.
  -x|--extract <deb> <directory>   Extract files.
  -X|--vextract <deb> <directory>  Extract & list files.
  --fsys-tarfile <deb>             Output filesystem tarfile.

  -h|--help                        Show this help message.
  --version                        Show the version.
  --license|--licence              Show the copyright licensing terms.

<deb> is the filename of a Debian format archive.
<cfile> is the name of an administrative file component.
<cfield> is the name of a field in the main `control' file.

Options:
  --showformat=<format>            Use alternative format for --show.
  -D                               Enable debugging output.
  --old, --new                     Select archive format.
  --nocheck                        Suppress control file check (build bad
                                     packages).
  -z#                              Set the compression level when building.
  -Z<type>                         Set the compression type used when building.
                                     Allowed values: gzip, bzip2, lzma, none.

Format syntax:
  A format is a string that will be output for each package. The format
  can include the standard escape sequences \n (newline), \r (carriage
  return) or \\ (plain backslash). Package information can be included
  by inserting variable references to package fields using the ${var[;width]}
  syntax. Fields will be right-aligned unless the width is negative in which
  case left alignment will be used.

Use `dpkg' to install and remove packages from your system, or
`dselect' or `aptitude' for user-friendly package management.  Packages
unpacked using `dpkg-deb --extract' will be incorrectly installed !
josh@media-server:~$ 

How does the command know where the file is anyway?

Thanks

---

### Post by PmDematagoda on 2008-01-24
You made a mistake in the command, it is:-
```
sudo dpkg [COLOR="Red"]**-i**[/COLOR] --force-architecture mce-installer_2.0.1-1_i386.deb
```
not
```
sudo dpkg [COLOR="Red"]**-**[/COLOR] --force-architecture mce-installer_2.0.1-1_i386.deb
```

---

### Post by Josh.Bolger on 2008-01-30
Sorry about the delayed response, here is what i got:


josh@media-server:~$ sudo dpkg -i --force-architecture mce-installer_2.0.1-1_i386.deb
dpkg: error processing mce-installer_2.0.1-1_i386.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mce-installer_2.0.1-1_i386.deb

Thanks

---

### Post by PmDematagoda on 2008-01-31
Post the output of:-
```
ls
```

---

