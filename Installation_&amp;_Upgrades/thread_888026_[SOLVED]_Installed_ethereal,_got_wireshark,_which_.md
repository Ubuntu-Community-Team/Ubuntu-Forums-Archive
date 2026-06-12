---
title: "[SOLVED] Installed ethereal, got wireshark, which won't un-install"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by arvevans on 2008-08-12
I installed ethereal using "sudo apt-get install ethereal".
What was installed is "wireshark", which is not what I wanted.
I then tried to remove it using "sudo apt-get remove ethereal" which found dependencies and apparently worked, but "wireshark" is still installed.

I then removed Wireshark "sudo apt-get remove wireshark"
Now no ethereal and no wireshark commands.

Trying again:
[INDENT]arv@arv-desktop:~$ sudo apt-get install ethereal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  guile-1.8 lilypond-data libdns32 python-editobj
  linux-headers-2.6.24-18-generic lilypond timidity libxbase2.0-0 dh-make
  linux-headers-2.6.24-16-generic alien linux-headers-2.6.24-16
  linux-headers-2.6.24-18 dpatch libxbsql0c2 texinfo
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  wireshark
The following NEW packages will be installed:
  ethereal wireshark
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/642kB of archives.
After this operation, 1606kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package wireshark.
(Reading database ... 407505 files and directories currently installed.)
Unpacking wireshark (from .../wireshark_1.0.0-1_i386.deb) ...
Selecting previously deselected package ethereal.
Unpacking ethereal (from .../ethereal_1.0.0-1_i386.deb) ...
Setting up wireshark (1.0.0-1) ...

Setting up ethereal (1.0.0-1) ...
arv@arv-desktop:~$ ethereal
bash: ethereal: command not found
arv@arv-desktop:~$ 
[/INDENT]

There is no "ethereal command, even though I thought I installed "ethereal".
_._

---

### Post by Partyboi2 on 2008-08-12
From what I understand wireshark use to be called ethereal, so wireshark should do what ethereal did.
To run it from the terminal you would type
wireshark
[[COLOR=Blue]Here[/COLOR]]("http://packages.ubuntu.com/hardy/ethereal") is the package details

---

### Post by arvevans on 2008-08-12
I can agree with that, but even if ethereal is now wireshark, why does removing ethereal not remove wireshark as well?  Seems that the system people still have a few bugs to work out.
_._

---

### Post by cariboo on 2008-08-12
Have you tried uninstalling wireshark, to see if ethereal is really installed in a terminal type:

```
locate ethereal
```

This should tell you if ethereal has really been installed.

Jim

---

### Post by arvevans on 2008-08-13
That is the problem...ethereal is not being installed.  Wireshark is being installed.  Un-installing ethereal does not un-install wireshark.  
_._

---

### Post by arvevans on 2008-08-21
Today's update fixed it.  Thanks.
_._

---

