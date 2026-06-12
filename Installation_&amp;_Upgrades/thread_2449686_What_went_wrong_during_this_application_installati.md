---
title: "What went wrong during this application installation?"
date: 2020-08-31
forum: Installation &amp; Upgrades
---

### Post by kieranfung on 2020-08-31
I recently installed a new application ([https://yade-dem.org/doc/installation.html](https://yade-dem.org/doc/installation.html)) for graduate school research and followed the instructions in the link. I thought everything was ready to launch, typed the command <yade> into my Ubuntu command line and received the following error:

#
kieran@DESKTOP-MQIQTVM:~/yade$ yade
Welcome to Yade 2020.01a
Using python version: 3.8.2 (default, Jul 16 2020, 14:00:26)
[GCC 9.3.0]
Traceback (most recent call last):
  File "/usr/bin/yade", line 144, in <module>
    import yade
  File "/usr/lib/x86_64-linux-gnu/yade/py/yade/__init__.py", line 75, in <module>
    from yade import boot
ImportError: libQt5Core.so.5: cannot open shared object file: No such file or directory
#

I'm new to Ubuntu, but I do recognize I could have established a hierarchy in my home directory for this new application. I was planning on establishing this new directory after I launched this application for a future work space. Is the lack of such a directory the reason why this app failed to launch? I'm not sure why this certain #libQt5Core.so.5# cannot be found otherwise. 

Any suggestions are much appreciated!

---

### Post by Holger_Gehrke on 2020-08-31
The page you link to gives three separate ways to install yade: from the Ubuntu repositories (older but stable version), from their own repository (daily build, probably less stable) and from source. If you did the last, did you read the warning about 2/3 of the way down on the page ?

> 
 Warning
 Only Qt5 is supported. On Debian/Ubuntu operating systems libQGLViewer of version 2.6.3 and higher are compiled against Qt5 (for other operating systems refer to the package archive of your distribution). If you mix Qt-versions a Segmentation fault will appear just after Yade is started. To provide necessary build dependencies for Qt5, install python-pyqt5 pyqt5-dev-tools.
 

Sounds a lot like what is happening on your system, doesn't it ?
If that's it, then a simple 'apt install python-pyqt5 pyqt5-dev-tools' should fix things, possibly after recompiling.

Holger

---

### Post by kieranfung on 2020-08-31
Hey Holger,

Thanks for reaching out and giving me your suggestion.

I went through with what you suggested and ran into the issue of installing the python-pyqt5 pyqt-dev-tools package. 

I went though the process to make sure this package was still in circulation - it is, noted here [https://packages.ubuntu.com/search?keywords=python-pyqt5&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=python-pyqt5&searchon=names&suite=focal&section=all). I then proceeded to add the universe + multiverse repositories, and updated apt after. However, the command "sudo apt install python-pyqt5 pyqt5-dev-tools" still does not work and the same error "the package is unable to be located" appears again. See below.

kieran@DESKTOP-MQIQTVM:~/yade$ sudo apt install python-pyqt5 pyqt5-dev-tools
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package python-pyqt5

I'm open to suggestions still. I feel as though I am missing something when trying to install these additional repositories, universal and multiverse, which is preventing me from installing this python package. 

Cheers,
Kieran

---

### Post by Holger_Gehrke on 2020-09-01
The search you link actually shows that python-pyqt5 doesn't exist on focal, it only shows python-pyqt5.qwt-doc (documentation for a widget kit based on qt5). What does exist is 'python3-pyqt5'. Since you are using a 3.x version of python this might be the package you need.

Holger

---

### Post by ActionParsnip on 2020-09-01
What is the output of
```

uname -a; lsb_release -a; apt-cache policy yade

```
Thanks

---

### Post by kieranfung on 2020-09-01
Hey ActionParsnip,

Thanks for engaging in the conversation.

Here's the output of the command you've suggested:

kieran@DESKTOP-MQIQTVM:~/yade$ uname -a; lsb_release -a; apt-cache policy yade
Linux DESKTOP-MQIQTVM 4.4.0-18362-Microsoft #836-Microsoft Mon May 05 16:04:00 PST 2020 x86_64 x86_64 x86_64 GNU/Linux
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 20.04.1 LTS
Release:        20.04
Codename:       focal
yade:
  Installed: 2020.01a-6build2
  Candidate: 2020.01a-6build2
  Version table:
 *** 2020.01a-6build2 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/universe amd64 Packages
        100 /var/lib/dpkg/status

What's the goal here? Are you trying determine the relationship between the codename + [COLOR=#000000]python-pyqt5?

Best,
Kieran[/COLOR]

---

### Post by kieranfung on 2020-09-01
Hey Holger,

I went through with what you've suggested and used the following command: sudo apt install python3-pyqt5

and got the following output:

kieran@DESKTOP-MQIQTVM:~/yade$ sudo apt install python3-pyqt5
[sudo] password for kieran:
Reading package lists... Done
Building dependency tree
Reading state information... Done
python3-pyqt5 is already the newest version (5.14.1+dfsg-3build1).
python3-pyqt5 set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 30 not upgraded.

Seems as though this step was redundant for the latest Ubtuntu version I downloaded ... Maybe not? 

I tried running the command "yade" again in attempt to launch the program again, but no luck. Still:

ImportError: libQt5Core.so.5: cannot open shared object file: No such file or directory

Any other suggestions I should explore?

Thanks for the assitance.

Kieran

---

### Post by Holger_Gehrke on 2020-09-03
That's strange. Your answer to ActionParsnip's question shows that you installed yade through the package manager, not by compiling it yourself. The error description on the installation page is meant for people who compile yade themselves, it should not happen with an installation from a package.

Have you checked whether libQt5Core.so exists ? Try 'locate libQt5Core.so', it should output a list of path and file names, usually in '/usr/lib/x86_64-linux-gnu/'. Since you installed from a package, it should have been pulled in as a dependency, but who knows ...

Holger

---

### Post by ualbino on 2020-09-03
I'm facing the same problem. When I tried to locate the libQt5Core.so, I got the following output:

ualbino@DESKTOP-BJV1SID:~$ locate libQt5Core.so
/usr/lib/x86_64-linux-gnu/libQt5Core.so.5
/usr/lib/x86_64-linux-gnu/libQt5Core.so.5.12
/usr/lib/x86_64-linux-gnu/libQt5Core.so.5.12.8

Since I'm new to Ubuntu and YADE, I have no idea what should I do to solve this issue. Any suggestions?

Thanks

Uilian

---

### Post by ualbino on 2020-09-04
Guys, I think i got the problem solved. Though, I'm not sure if everthing is fine because I have never used YADE before. I have just installed for graduate school research.

In order to solve the issue you need to open the file "..yade/__init__.py" and include the code "import PyQt5.QtCore" just before the "from yade import boot" where the issue is rising.

Best regards,
Uilian

---

