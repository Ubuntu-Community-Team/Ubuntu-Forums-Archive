---
title: "Unable to boot Ubuntu 12.04 after Boot-repair"
date: 2014-03-19
forum: Installation &amp; Upgrades
---

### Post by martin73 on 2014-03-19
[http://paste.ubuntu.com/7121943/](http://paste.ubuntu.com/7121943/)

Hello,
I have increased the size of the Windows 7 partition but it failed to boot. I have run boot-repair from a live cd and now the pc only boots Windows. In the Windows file manager the linux partition appears empty. Does anybody have a solution?
Thanks.

Bye, Martin

---

### Post by ajgreeny on 2014-03-19
I'm afraid you don't have a Ubuntu partition, only an extended partition, sda4, with swap, sda5,  inside it.
```
/dev/sda4       198907885   202958847     2025481+   5  Extended
/dev/sda5       198907904   202958847     2025472   82  Linux swap / Solaris
```
How did you extend your windows partition as it looks as if you might have used the Ubuntu space to do so?

By the way, windows disk manager will always show a Ubuntu or other Linux partition as being empty as it can not read any Linux filesystems.

---

### Post by martin73 on 2014-03-20
Thanks. I have used EaseUS in Windows. sda4 was a larger unused partition except for the linux swap (sda5) inside it. I have decreased the size of sda4 such that it matches the size of sda5. Ubuntu is installed on sda3.

---

### Post by ajgreeny on 2014-03-20
I have no knowledge of EaseUS but assume it is a partition editor/manager like gparted, and I think I understand what you did with sda4 and sda5, but why did you do that, which partition was your windows 7 partition, and what happened to it?

I am confused!

---

### Post by LostFarmer on 2014-03-20
did you install linux on a NTFS partition ?  sda3 is NTFS and has linux as it label.  Did you do a wibi install ?

---

### Post by martin73 on 2014-03-21
Windows is in sda2. Ubuntu is installed on sda3. sda3 was created by the Ubuntu live cd, although I had originally reserved sda4 for a Linux installation. Therefore, I reduced the size of sda 4 to have more space on sda2.
It seems to be very confusing, so I am now thinking of securing my data on Ubuntu partition using Ubuntu from the live dvd. Then I can completely remove sda3, sda4 and sda5 and do a new installation of Ubuntu. Do you think that this would work? And what about grub, where is it installed?
(I am trying to keep the windows installation since it is a lot of work to install whereas Ubuntu is installed rather easily.)

---

### Post by ajgreeny on 2014-03-21
Sorry, I made a whoopsie in post #4; instead of asking where your windows partition was I meant your ubuntu partition, which is not present as a separate partition, so you appear not to have ubuntu installed unless, as suggested by LostFarmer, you installed Ubuntu with wubi, ie inside your running Windows 7 OS.

To have a proper dual boot you need to power-off then cold boot to the DVD or USB, choose "Try without installing" to check that everything works and then do the installation after a double click on the Install Ubuntu icon.

So we know exactly what is going on here can you please boot to a live ubuntu desktop, run **sudo fdisk -l** in terminal and report the output back here, and also if possible show us a screenshot of the gparted window from the live system.

---

### Post by martin73 on 2014-03-22
I have merged all partitions into the Windows partition and reinstalled Ubuntu. Now it is working fine again. Apparently, the tool I used for repartitioning, EaseUS, did not do a good job.
Thanks.

---

