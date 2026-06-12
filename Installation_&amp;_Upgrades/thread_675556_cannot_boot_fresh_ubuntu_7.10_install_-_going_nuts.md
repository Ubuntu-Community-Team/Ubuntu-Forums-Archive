---
title: "cannot boot fresh ubuntu 7.10 install - going nuts on this :("
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by jabibi on 2008-01-22
Hello guys this is my first post and sadly it is to ask for help for a problem i have not been able to solve on my own, I've looked all over this forum and google for a solution but havent found one yet

first of all my pc specs:
amd athlon 64 x2 4200 2,2 GHz
1 GB ram
nvidia 7300 512 MB
Biostar Motherboard with Nvidia Chipset
and the most important in this case: 1 SATA hard drive and 1 IDE hard drive

well i got windows in the SATA drive and I am installing ubuntu 7.10 gutsy on the IDE drive
installation goes all okay

PROBLEM: when i boot i get to Grub and select linux instead of windows, then it gets to the ubuntu logo screen and the hard drive read led sometimes blinks very briefly and most times doesnt even blink at all and it just stays there without loading anything for a while then throwing me to a busybox prompt

I think the problem is that my IDE hard drive is not accesible i have reached this conclusion becase when i use live cd and try to mount the IDE drive (hda) where i installed ubuntu and i go to /dev/ i find that there is no hda1 nor hda2 nor anything just one hda file that i dont know what to do with. curious thing is that the sata drive with the ntfs partition is okay because i can totally find the sda1 file under /dev/ folder

plus here's a screenshot of an error i get with GParted while using the live cd

i tried to find a solution for this but wasnt successful & i'm totally clueless now

it seems that the hda drive is blocked for some reason and keeps it from creating the hda1 file or something i dont know, already tried to set the jumpers, didnt work


I can get on a live cd but i cannot access hda1 (main boot partition for ubuntu) at all as a consequence of that I cannot access /etc/fstab file

And this is how i set up my hard drives: SATA drive completely partitioned with NTFS for windows, IDE drive completely used for ubuntu ext3 partition only 2.8 GB for swap


thank you guys for reading it came out longer than i tought

[IMG]http://img115.imageshack.us/img115/1374/parterrorcc8.png[/IMG]

---

### Post by PurposeOfReason on 2008-01-22
Assuming you did install on the ide drive, the problem may be it's not on your fstab. If you could get on a live cd, browse through the install, and look for the /etc/fstab file someone might be able to help you. It would also make it easier if you posted exactly how you have your harddrives and partitions set up.

---

### Post by wolfen69 on 2008-01-22
while using the live cd and using gparted, you must be root to make changes.

open terminal in live cd.
```
sudo su
```
then
```
gparted
```
there is a pull down menu at the top right in gparted (where it says /dev/hda1 or whatever)
your sata drive should be there.

---

### Post by jabibi on 2008-01-22
hey wolfen thanks for replying but you got a bit confused, i can totally access my sata drive its the ide one that i cannot access, "sda" and "sda1" files exist under /dev/ but there is only hda but there is **Not any "hda1"** like there should be
also tried running gparted as root like you said, didnt solve anything

---

### Post by jabibi on 2008-01-24
fixed, i changed the IDE cable... who wouldve tought

---

