---
title: "Ubuntu 12.04 Blank Screen after rebooting"
date: 2013-07-30
forum: Installation &amp; Upgrades
---

### Post by GkxJLMG on 2013-07-30
Hello everyone, 
After installing ubuntu server 12.04 with no errors, It rebooted, as per install.
On the reboot, It boots up fine, dell splash screen pops up, and it boots up...
into a blank screen! Woohoo!
I can tell it is sending a signal... Which happens to be a blank screen.
Any help would be appreciated.
-icecube45
Also, its not just me is it, my username is [**[COLOR=#000000]GkxJLMG[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841844")?

---

### Post by mojo706 on 2013-07-31
Hello, there is a comprehensive guide (more than could fit here) on how to solve the Blank screen after booting issue apparently its not you alone :D. Here is the link [[SIZE=2]Graphics Resolution- Upgrade /Blank Screen after reboot[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1743535") . Read and follow the instructions carefully and may find the answer :).

---

### Post by GkxJLMG on 2013-07-31
> **mojo706 said:**
> Hello, there is a comprehensive guide (more than could fit here) on how to solve the Blank screen after booting issue apparently its not you alone :D. Here is the link [[SIZE=2]Graphics Resolution- Upgrade /Blank Screen after reboot[/SIZE]]("http://ubuntuforums.org/showthread.php?t=1743535") . Read and follow the instructions carefully and may find the answer :).

booting up the livecd, it does not recognize that there is ubuntu installed..

---

### Post by Bashing-om on 2013-07-31
GkxJLMG; Hi !

In that case show us what the disk(s) partitioning is presently. From the liveDVD submit the output of terminal codes:
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```

[INDENT][INDENT]a tale in the telling
[/INDENT][/INDENT]

---

### Post by GkxJLMG on 2013-07-31
> **Bashing-om said:**
> GkxJLMG; Hi !

In that case show us what the disk(s) partitioning is presently. From the liveDVD submit the output of terminal codes:
```

sudo fdisk -lu 
sudo parted -l
sudo parted /dev/sda unit s print
lsblk -f

```
[INDENT][INDENT]a tale in the telling
[/INDENT]
[/INDENT]


So that really is my name... odd... 

well, as I recieved this, I am currently installing it to a spare harddrive on the same computer, to test whether it was a bad drive.
I'll let you know asap

---

### Post by GkxJLMG on 2013-07-31
Scratch that!
Tried the disk I installed to on another computer, it booted up to the grub menu, odd, I'll let you know the disk partitioning asap

---

### Post by Iowan on 2013-07-31
> **GkxJLMG said:**
> 
-icecube45
Also, its not just me is it, my username is [**[COLOR=#000000]GkxJLMG[/COLOR]**]("http://ubuntuforums.org/member.php?u=1841844")?

If you had an account and lost access to it, you can start a thread in the Resolution Centre, and we'll try to help you reconnect with your old account.

---

