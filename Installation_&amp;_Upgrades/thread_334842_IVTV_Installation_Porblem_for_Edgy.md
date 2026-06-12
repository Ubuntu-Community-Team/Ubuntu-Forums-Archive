---
title: "IVTV Installation Porblem for Edgy"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by carlb on 2007-01-09
I am installing a Hauppage 150 card on a older Biostar IDEQ SFF system.  My system is a fresh instal of Ubuntu  6.10.  I am following the installation procedure outlined in this web page:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

I am getting the error    devscripts: command not found

Here is my session text:



cb@iqeqtv:~$ sudo apt-get install ivtv-source 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpatch dpkg-dev html2text module-assistant
Suggested packages:
  dh-make curl debian-keyring build-essential
Recommended packages:
  fakeroot patchutils
The following NEW packages will be installed:
  debhelper dpatch dpkg-dev html2text ivtv-source module-assistant
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1010kB of archives.
After unpacking 3019kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7 [110kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main debhelper 5.0.37.3ubuntu4 [508kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpatch 2.0.20 [84.1kB]            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe module-assistant 0.10.6 [80.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse ivtv-source 0.7.0-2 [133kB] 
Fetched 1010kB in 22s (45.3kB/s)                                               
Selecting previously deselected package dpkg-dev.
(Reading database ... 88317 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.37.3ubuntu4_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.20_all.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.6_all.deb) ...
Selecting previously deselected package ivtv-source.
Unpacking ivtv-source (from .../ivtv-source_0.7.0-2_all.deb) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up dpatch (2.0.20) ...
Setting up module-assistant (0.10.6) ...
Setting up ivtv-source (0.7.0-2) ...
cb@iqeqtv:~$ devscripts ivtv-utils 
bash: devscripts: command not found
cb@iqeqtv:~$ 

Your advice is appreciated.

---

### Post by superm1 on 2007-01-09
> **carlb said:**
> I am installing a Hauppage 150 card on a older Biostar IDEQ SFF system.  My system is a fresh instal of Ubuntu  6.10.  I am following the installation procedure outlined in this web page:
[https://help.ubuntu.com/community/Install_IVTV_Edgy](https://help.ubuntu.com/community/Install_IVTV_Edgy)

I am getting the error    devscripts: command not found

Here is my session text:



cb@iqeqtv:~$ sudo apt-get install ivtv-source 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpatch dpkg-dev html2text module-assistant
Suggested packages:
  dh-make curl debian-keyring build-essential
Recommended packages:
  fakeroot patchutils
The following NEW packages will be installed:
  debhelper dpatch dpkg-dev html2text ivtv-source module-assistant
0 upgraded, 6 newly installed, 0 to remove and 0 not upgraded.
Need to get 1010kB of archives.
After unpacking 3019kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpkg-dev 1.13.22ubuntu7 [110kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main html2text 1.3.2a-3 [95.5kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main debhelper 5.0.37.3ubuntu4 [508kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpatch 2.0.20 [84.1kB]            
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe module-assistant 0.10.6 [80.5kB]
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/multiverse ivtv-source 0.7.0-2 [133kB] 
Fetched 1010kB in 22s (45.3kB/s)                                               
Selecting previously deselected package dpkg-dev.
(Reading database ... 88317 files and directories currently installed.)
Unpacking dpkg-dev (from .../dpkg-dev_1.13.22ubuntu7_all.deb) ...
Selecting previously deselected package html2text.
Unpacking html2text (from .../html2text_1.3.2a-3_i386.deb) ...
Selecting previously deselected package debhelper.
Unpacking debhelper (from .../debhelper_5.0.37.3ubuntu4_all.deb) ...
Selecting previously deselected package dpatch.
Unpacking dpatch (from .../archives/dpatch_2.0.20_all.deb) ...
Selecting previously deselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.10.6_all.deb) ...
Selecting previously deselected package ivtv-source.
Unpacking ivtv-source (from .../ivtv-source_0.7.0-2_all.deb) ...
Setting up dpkg-dev (1.13.22ubuntu7) ...
Setting up html2text (1.3.2a-3) ...

Setting up debhelper (5.0.37.3ubuntu4) ...
Setting up dpatch (2.0.20) ...
Setting up module-assistant (0.10.6) ...
Setting up ivtv-source (0.7.0-2) ...
cb@iqeqtv:~$ devscripts ivtv-utils 
bash: devscripts: command not found
cb@iqeqtv:~$ 

Your advice is appreciated.
You've just got a minor typo.

it should be:
```
sudo apt-get install ivtv-source devscripts ivtv-utils module-assistant
```All in one line.  You somehow lost the others to another line.

---

### Post by carlb on 2007-01-11
Thanks for pointing that out.  It certainly  was the problem.  I was copying/pasting the commands from the help text and didn't realize that I had narrowed the browser page causing the box with the command to appear as two lines.

---

