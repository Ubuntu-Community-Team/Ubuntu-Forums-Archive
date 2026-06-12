---
title: "How to resume upgrade to 18.10 through konsole?"
date: 2018-10-19
forum: Installation &amp; Upgrades
---

### Post by n0umenon on 2018-10-19
Hi,

I was attempting an upgrade to the new 18.10 LTS version of Kubuntu through konsole. In the process, I was asked if I need the packages which are unneeded to be deleted. There were three options: Y, N, and Details. I choose "Details", but didn't know how to get back after the list came to the foreground, so I hit the combination ctrl+z, that terminated the whole process. While I was trying to get back to the process through the "fg" command, the konsole closed unexpectedly and now I can't even reboot my system because of a problem with ksmserver-logout-greeter...

Any idea how to get back at the upgrading process without any bad consequences?

---

### Post by deadflowr on 2018-10-19
None of that sounds good.
Can you boot into a recovery mode?
[https://wiki.ubuntu.com/RecoveryMode]("https://wiki.ubuntu.com/RecoveryMode")

In recovery mode there is an option to repair broken packages, you might try that.

Your system is basically half installed.
Repair broken packages might install the other half.
Or it might not.
But it is something to try for starters.

---

### Post by n0umenon on 2018-10-19
Hello again, 

When I get into grub I saw this: 

Ubuntu, with Linux 4.18.0-10-generic 
Ubuntu, with Linux 4.18.0-10-generic (recovery mode) 
Ubuntu, with Linux 4.15.0-38-generic 
Ubuntu, with Linux 4.15.0-38-generic (recovery mode)


I tried the both "recovery mode" versions, but when I attempt the "Repair broken packages" option I've received this message:


[HTML]/lib/recovery-mode/recovery-menu: line 80: /etc/default/rcS: No such file or directory 
^[[C^[[D 
Reading cache 

Can not upgrade 

Your python install is corrupted. Please fix the '/usr/bin/python' symlink. 
[/HTML]


Sounds bad to me..

---

### Post by #&amp;thj^% on 2018-10-19
Try with this first:
```
sudo apt-get install --reinstall python
```
Now try again with fix broken

---

### Post by n0umenon on 2018-10-19
Thank you for your suggestion, but the message is the same...

---

