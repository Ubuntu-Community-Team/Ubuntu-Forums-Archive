---
title: "DEVED INSTALL error 1? help!!"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by pv2smurf on 2010-01-24
[FONT=Times New Roman][SIZE=3]I'm COMPLETELY new to linux. I"m running Ubuntu 9.10 and TRYING to install Devede. I have tried the Terminal, Synaptic Manger, and the Add/Remove and still keep getting this same error. I'm running a regular 32 bit Pentium 3 process to test if I like Linux or not.

this is what it says:

[B]E: /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb: corrupted filesystem tarfile - corrupted package archive
[/B]


this is not a DUAL boot computer either.


help please?

[EMAIL="pv2smurf@yahoo.com"]pv2smurf@yahoo.com[/EMAIL][/SIZE][/FONT]

---

### Post by mikewhatever on 2010-01-24
[Howto fix a broken package]("https://help.ubuntu.com/community/SynapticHowto#How%20to%20fix%20broken%20packages")

Alternatively, run **sudo apt-get -f install**

---

### Post by pv2smurf on 2010-01-24
tried that THEN did a reinstall through terminal still tells me I"m missing mplayer and mencoder.

tried 

sudo apt-install mplayer and GOT nothing

any another help?

---

### Post by pv2smurf on 2010-01-24
and tried the fix broken package link and I get this

E: /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb: corrupted filesystem tarfile - corrupted package archive

so what could I do now?

---

### Post by mikewhatever on 2010-01-24
Well, apt-install is not a valid command. Can you post the output of the following one (close Synaptic first):

sudo apt-get install devede

---

### Post by pv2smurf on 2010-01-25
here's what I got:

smurf@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec-extra-52
The following NEW packages will be installed:
  libavcodec-extra-52
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/4,004kB of archives.
After this operation, 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154087 files and directories currently installed.)
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
smurf@ubuntu:~$ sudo apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
devede is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  devede: Depends: libavcodec-extra-52 but it is not going to be installed
  gstreamer0.10-ffmpeg: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                                 libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  libavformat-extra-52: Depends: libavcodec-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
                        Depends: libavcodec-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
  libquicktime1: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                          libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  mencoder: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                     libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  mplayer-nogui: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                          libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).



AFTER I try 'apt-get -f install'  I get this:

smurf@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libavcodec-extra-52
The following NEW packages will be installed:
  libavcodec-extra-52
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 0B/4,004kB of archives.
After this operation, 11.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 154087 files and directories currently installed.)
Unpacking libavcodec-extra-52 (from .../libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
smurf@ubuntu:~$ sudo apt-get install devede
Reading package lists... Done
Building dependency tree       
Reading state information... Done
devede is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  devede: Depends: libavcodec-extra-52 but it is not going to be installed
  gstreamer0.10-ffmpeg: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                                 libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  libavformat-extra-52: Depends: libavcodec-extra-52 (>= 4:0.5+svn20090706) but it is not going to be installed
                        Depends: libavcodec-extra-52 (< 4:0.5+svn20090706-99) but it is not going to be installed
  libquicktime1: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                          libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  mencoder: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                     libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
  mplayer-nogui: Depends: libavcodec52 (>= 3:0.svn20090303-1) but it is not going to be installed or
                          libavcodec-extra-52 (>= 3:0.svn20090303-1) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by mikewhatever on 2010-01-26
Well, I am really not sure. Since fixing the broken package doesn't seem to woks, lets try deleting it, just the offending one.

sudo rm /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb

Then try over again.

sudo apt-get update
sudo apt-get -f install

---

### Post by pv2smurf on 2010-01-26
mikewhatever it worked thanks a whole bunch!!!  everytime I would type the:
 
sudo rm /var/cache/apt/archives/libavcodec-extra-52_4%3a0.5+svn20090706-2ubuntu3_i386.deb

wouldn't work. don't think the command is valid but after I typed:

sudo apt-get install devede - I kept getting error 1 as explained above.

sudo apt-get update THEN
sudo apt-get -f install

WORKED LIKE A CHARM!!

so my assumption is that sudo apt-get -f install IS the command to FORCE the install in the terminal?

---

### Post by mikewhatever on 2010-01-26
Yeah, but you've run <apt-get -f install> before, and it didn't quite work. The command to delete the file only needs to be entered once, cause after the first time, the file is no longer there, so you'd get an error.

---

