---
title: "Root Password &amp; Sudo command fail bug report"
date: 2007-11-30
forum: Installation &amp; Upgrades
---

### Post by pjping on 2007-11-30
Hi guys,

    After install V7.10 Server, I try to enable root account and set the root password.

nano@mylinux:~$ sudo passwd
[sudo] password for nano:
nano is not the sudoers file. This incident will be reported.
nano@mylinux:~$ sendmail: fatal: open /etc/postfix/main.cf: No such file or directory


Could you do me a favour?

:popcorn:

---

### Post by Pumalite on 2007-11-30
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by n1ym on 2007-11-30
I am still pretty much a beginner with the command line, but i do I have more or less the same problem.

After installation of the Server 7.10 i do log into the console with the username that I registered during the installation. 

However everytime I try to start a *sudo* command and put in my password i get the following:

[I]wolfgang@Server1:~$ sudo shutdown -h 0
[sudo] password for wolfgang:
wolfgang is not in the sudoers file. This incident will be reported.[/I]

It appears that during the installation the username was not written to the appropriate authentication files. Now I can't even shut down the system!!

Any help is greatly appreciated!!

Wolfgang

---

### Post by n1ym on 2007-12-01
Well, after a day of frustration I gave up on this. 

It appears that the installation routine for Server 7.10 did not write the appropriate permissions into the /etc/sudoers file. Unfortunately I was not able to edit this file. In addition the RAID arrays that I did setup with this installation routine appeared to be unstable.

I now installed Server 6.06 and everything is working fine. Sudo is accessible.

If anybody can come up with an idea why sudo is not working on 7.10 please let me know.

W.

---

