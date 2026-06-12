---
title: "Only Memtest after deleting old kernels"
date: 2015-12-22
forum: Installation &amp; Upgrades
---

### Post by qwyrp on 2015-12-22
I deleted some old kernels but something went wrong. My server now only starts up in Memtest mode. I've tried it with Boot-repair (Recommend options) and after hours (> 4) of purging I stopped it. I managed to get some info from Boot-repair and they suggest to get help from forums. Here's is the log-file [http://pastebin.ubuntu.com/14137017/plain/]("http://pastebin.ubuntu.com/14137017/plain/") and hopefully somebody can save me.
- ubuntu server 14.04 - 64b

---

### Post by ian-weisser on 2015-12-22
What was the method (or exact sequence of commands) you were using to delete old kernels?
Was this normal maintenance, or were you responding to a warning or error?

---

### Post by qwyrp on 2015-12-22
Something like *uname -r* and *sudo apt-get autoremove linux-image-* * where * was the old kernels (at least this was supposed to be old).
There was no warning or error and pure maintenance

---

### Post by Bashing-om on 2015-12-22
qwyrp; Hello;

Ouch ! Is the server still running ? You have not re-booted, have you.

If still running, maybe we can get a fix:
For starters :
Post back - Between code tags - these terminal command outputs:
```

uname -r
dpkg-l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/
ls -al /vmlinuz*
ls -al /initrd.img*
ls -al /boot
df -h
df -i

```
To give us an idea of what we are working with and what we are working toward.
 
This may get real
[INDENT][INDENT][INDENT][INDENT]interesting
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mörgæs on 2015-12-23
> **qwyrp said:**
> Something like *uname -r* and *sudo apt-get autoremove linux-image-* * where * was the old kernels (at least this was supposed to be old).
There was no warning or error and pure maintenance

The safe command is *sudo apt-get autoremove *without mentioning kernels.

---

### Post by qwyrp on 2015-12-23
I've already rebooted and that why I'm knowing I'm in trouble

---

### Post by steeldriver on 2015-12-23
You should be able to install a kernel from a chroot environment: see 

[http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels](http://askubuntu.com/questions/28099/how-to-restore-a-system-after-accidentally-removing-all-kernels) 

for example

---

### Post by qwyrp on 2015-12-23
Okay this is probably not working because I'm also using LVM (sorry forget to mention this:oops:

---

### Post by Skaperen on 2015-12-23
it's obvious to me that *all* kernels got deleted as all that is remaining is *memtest*.  rescue disk time.  do you still have the CD/media that was originally used to do the install?  if so,  see if it will boot (choose it in BIOS) and let us know.

---

### Post by qwyrp on 2015-12-23
I don't have the original CD/media but I've checked it with Ubuntu LiveCD and it's bootable

---

### Post by steeldriver on 2015-12-23
> **qwyrp said:**
> Okay this is probably not working because I'm also using LVM (sorry forget to mention this:oops:

Do you know what the issue is with LVM exactly? Pretty sure I've done it on an LVM based system (in fact I'm pretty sure that's the ONLY time I've done it) - although my memory may be failing me.

Shouldn't it just be a matter of making sure the lvm2 package is installed on the live system, then identifying the correct /dev/mapper/vgwhatever--lvwhatever for the / filesystem (using blkid / parted / fdisk)?

---

