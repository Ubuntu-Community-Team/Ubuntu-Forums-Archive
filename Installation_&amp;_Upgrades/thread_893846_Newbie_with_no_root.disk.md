---
title: "Newbie with no root.disk"
date: 2008-08-18
forum: Installation &amp; Upgrades
---

### Post by lincolnspector on 2008-08-18
Hi, everyone. I'm pretty experienced with Windows, but a novice with Linux.

I just installed ubuntu onto a Windows XP system. But when I boot into ubuntu, I get a (initramfs) command prompt.

If I select the recovery mode, a message tells me that 

[INDENT]ALERT! /host/ubuntu/disks/root.disk does not exist. Dropping to a shell![/INDENT]

I've rebooted into Windows, uninstalled then reinstalled ubuntu, and tried again. Same result.

Any ideas?

Lincoln

---

### Post by eggie9001 on 2008-08-18
Is your ubuntu folder in c:/?

---

### Post by lincolnspector on 2008-08-18
A quick update:

I should mention that this is a PC I use exclusively for testing software. It has four primary partitions, and at any given time 3 of them are hidden. I installed ubuntu into the 3rd partition, which runs XP Home.

After that last post, I restored that partition from an image and tried again. This time, in the after-the-reboot part of the Ubuntu installation, just after it asked me my time zone, it came up with an error message:

[INDENT]Partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.[/INDENT]

The first time this happened, I picked "Try again," and after about half an hour, abandoned the installation. 

Lincoln

---

### Post by lincolnspector on 2008-08-18
Yes, it is.

Thanks,

Lincoln

---

### Post by lincolnspector on 2008-08-18
> **lincolnspector said:**
> A quick update:

I should mention that this is a PC I use exclusively for testing software. It has four primary partitions, and at any given time 3 of them are hidden. I installed ubuntu into the 3rd partition, which runs XP Home.

After that last post, I restored that partition from an image and tried again. This time, in the after-the-reboot part of the Ubuntu installation, just after it asked me my time zone, it came up with an error message:

[INDENT]Partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.[/INDENT]

The first time this happened, I picked "Try again," and after about half an hour, abandoned the installation. 

Lincoln
Now here's something interesting. When I boot into Ubuntu, it attempts to complete the installation and fails as described above.

Then ubuntu loads.

What's missing? i don't know. But in places, I see three of the four NTFS partitions on this hard drive. The one I don't see is the one I installed ubuntu into. 

Lincoln

---

### Post by shantanubhadoria on 2008-10-30
I have the same problem I installed Hardy on a NTFS Partition today I accidentally did a hard reboot and somehow /host/ubuntu/disks/root.disk is unusable. This happened to me earlier too when my laptop shut down due to battery loss. however it somehow recovered on its own later. Please note that root.disk is still there but somehow ubuntu cannot use it.
please let me know if there is anyway to fix this . . . 
this is a fairly frequent thing with wubi install from the forums I saw.
there must be some way to check and fix the file.

---

### Post by shantanubhadoria on 2008-10-30
Ok here is something you guys could try . . .

boot up in windoz and fire the command prompt
go to the drive where the wubi/ubuntu is installed
I: for me

>I:

then run 'chkdsk /r'
I:>chkdsk /r

if you are lucky the damage is not big. I had a couple of bad clusters and rougue indexes. 
Best of luck :)
-----------------------------------------------------------------------------------------
Correction don't do this chkdsk ended up removing my root.disk for errors. I suffered mega damage to my work and deadlines.

---

