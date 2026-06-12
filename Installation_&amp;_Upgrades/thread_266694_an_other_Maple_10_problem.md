---
title: "an other Maple 10 problem"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by themijs on 2006-09-27
Hi,

I'm trying to install maple 10 on my computer (Dapper drake i386)
But it won't work.

This is what I did for installing maple 10


```
themijs@TheMijs:~$ tar -zxvf maple10.tar.gz

./
./Install.html
./installMapleLinuxSU
./Linux/
./Linux/Disk1/
./Linux/Disk1/InstData/
./Linux/Disk1/InstData/MediaId.properties
./Linux/Disk1/InstData/Resource1.zip
./Linux/Disk1/InstData/VM/
./Linux/Disk1/InstData/VM/LinuxInstaller.bin
./Linux/readme.txt
themijs@TheMijs:~$ ./Linux/Disk1/InstData/VM/LinuxInstaller.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
./Linux/Disk1/InstData/VM/LinuxInstaller.bin: line 2087: strings: command not found

Launching installer...
```

after I completed the installer

```
themijs@TheMijs:~$ xmaple
bash: xmaple: command not found

```

or

```
themijs@TheMijs:~$ maple
bash: maple: command not found
```

and in the map there isn't a program

```
themijs@TheMijs:~$ ls maple10
afm                  ia_jre_extraction_dir_9854.tmp  Maple_10_InstallLog.log
bin                  Install.html                    readme.txt
bin.IBM_INTEL_LINUX  java                            samples
data                 jre.IBM_INTEL_LINUX             test
etc                  lib                             X11_defaults
examples             license
extern               man
```

what did I do wrong?

Why maple won't run/work?

Thanks in advance for your time

---

### Post by sexcopter on 2006-09-30
It's in the bin folder, so

```
cd ./bin
./xmaple
```

should work, I think. I'm doing this from memory, 'cos I'm using Edgy now, and can't seem to install it here, I get the following and wonder if anyone can help me:

```
james@james-laptop-edgy:/cdrom$ sudo sh installMapleLinuxSU 
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...
nawk: error while loading shared libraries: libm.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/bin/ls: error while loading shared libraries: librt.so.1: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
dirname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
basename: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
hostname: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory

Launching installer...

grep: error while loading shared libraries: libc.so.6: cannot open shared object file: No such file or directory
/tmp/install.dir.7052/Linux/resource/jre/bin/java: error while loading shared libraries: libpthread.so.0: cannot open shared object file: No such file or directory
```

Tried installing libc-dev, but no joy.

---

### Post by bernd_d on 2006-10-03
I have the same problem like sexcopter ](*,) 
A working solution would be great!

---

