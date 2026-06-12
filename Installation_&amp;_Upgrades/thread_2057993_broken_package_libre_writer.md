---
title: "broken package libre writer"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by Sonoran Desert Rat on 2012-09-14
This is my second install ever (firefox went smooth). This is happening:

DELETED USER NAME:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libreoffice : Depends: libreoffice-writer but it is not installed
E: Unmet dependencies. Try using -f.
DELETED USER NAME:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libreoffice-writer
Suggested packages:
  libreoffice-gcj libreoffice-filter-binfilter
The following NEW packages will be installed:
  libreoffice-writer
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/7,626 kB of archives.
After this operation, 20.6 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 128060 files and directories currently installed.)
Unpacking libreoffice-writer (from .../libreoffice-writer_1%3a3.5.4-0ubuntu1.1_i386.deb) ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb (subprocess): data: internal bzip2 read error: 'UNEXPECTED_EOF'
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libreoffice-writer_1%3a3.5.4-0ubuntu1.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/program/libmswordlo.so'
No apport report written because MaxReports is reached already
                                                              Processing triggers for desktop-file-utils ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libreoffice-writer_1%3a3.5.4-0ubuntu1.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

I am on Lubuntu, but all the other libre apps are installed and working.
Help please?

---

### Post by marinara on 2012-09-16
i might be too noob to help you, but why are you doing 
apt-get upgrade?

especially on a new install?

---

### Post by marinara on 2012-09-16
this was what you posted.  it looks like some kind of file system error?

dpkg-deb (subprocess): data: internal bzip2 read error: 'UNEXPECTED_EOF'
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/program/libmswordlo.so'
No apport report written because MaxReports is reached already

---

### Post by jerrrys on 2012-09-16
In terminal:

sudo apt-get clean

sudo apt-get update

sudo apt-get upgrade

Did that fix it??

---

### Post by tienlbhoc on 2012-09-16
> **marinara said:**
> this was what you posted.  it looks like some kind of file system error?

dpkg-deb (subprocess): data: internal bzip2 read error: 'UNEXPECTED_EOF'
 short read on buffer copy for backend dpkg-deb during `./usr/lib/libreoffice/program/libmswordlo.so'
No apport report written because MaxReports is reached already

yes, this mean, download not 100% or EOF (end of file) error

---

### Post by Sonoran Desert Rat on 2012-09-16
> **jerrrys said:**
> In terminal:

sudo apt-get clean

sudo apt-get update

sudo apt-get upgrade

Did that fix it??

...
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en
Fetched 81.7 kB in 3s (25.3 kB/s)
Reading package lists... Done
DELETED$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
DELETED$ 

I have been busy, finally got a chance to get back to this. Thank you! I ran all three. I had a broken dependency in Synaptic too. It seems to be gone and my program is running fine except that Libre Office will run any document except the word processor.

---

