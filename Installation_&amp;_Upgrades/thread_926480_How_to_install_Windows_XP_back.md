---
title: "How to install Windows XP back"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by khictvak on 2008-09-22
Hello everyone, I am a Ubuntu newbie. So here the problems.

I used Windows XP. Later, I installed Ubuntu 8.04 in it (Wubi). Then, I made decision to delete Ubuntu and Windows XP because I want to install fresh Windows XP.

I deleted all the partitions, but my 80GB HDD only show 74.5GB. Then, when I try boot from WIndows XP CD, after screen shows

"Setup is inspecting your computer’s hardware configuration”

the computer will restart and restart again. when i try to install Ubuntu or Vista, there no such problem like this. any idea to solve this problem? thanks.

---

### Post by khictvak on 2008-09-22
can any one help me? please... :cry:

---

### Post by wolterh on 2008-09-22
Well, do you get any other error, or output that you can specify here at the forums?

Personally I would like to ask you, why do you want XP back?

---

### Post by khictvak on 2008-09-22
If it's pass that message ("Setup is inspecting your computer’s hardware configuration”), several second later another error appeared. it sound like this:

"Cannot load the file \i386\NTKRULMP.EXE into memory. Error code is 7.
Setup cannot continue. Press a key to close the installation programme."

well, I dont have internet connection. so it's very hard for me to instal ubuntu plugins. plus my sister always compalin she doesn't know how to use Ubuntu.

---

### Post by wolterh on 2008-09-22
My first guess is that your CD is corrupt. Now, I am not saying that you are subject of piracy, but maybe its got a scratch or something that makes some of its data unreadable.

About your sister... I even think that ubuntu is easier to use! And besides.. what does she do in the computer that makes it so difficult for her to do it in ubuntu? Well, never mind--thats non of my business...

Summary: Get a new disk, or clean it (its ok with water and soap, but be careful not to push too hard with a towel when drying)

Recommendation: Install ubuntu haha

---

### Post by prshah on 2008-09-22
> **khictvak said:**
> 
I deleted all the partitions, but my 80GB HDD only show 74.5GB. Then, when I try boot from WIndows XP CD,
the computer will restart and restart again. when i try to install Ubuntu or Vista, there no such problem like this. 

The 74.5 GB is normal, that is because manufacturers trean GB as (10^10) instead of the correct GiB (2^30).

The capacity reading is correct.

If you're using a SATA drive, then XP (prior to SP3) has trouble with those since SATA drivers are not available in XP SP2 and below. Now you can:

a) Get XP SP3
b) Slipstream the correct SATA drivers for your motherboard into the XP installation you have
c) Press F6 at the beginning of the installation when asked to install custom drivers (and have a floppy with the motherboard's SATA device driver)
d) Check in BIOS for SATA options such as "Native Mode", "Legacy Mode", "IDE Compatible mode", etc. (The option varies from BIOS to BIOS, so I cannot be more specific).

The (d) option is quickest for you, but will slightly degrade performance, so once your XP is all setup (and updated), change the option back to whatever it was originally.

If none of these are suitable for you, install Ubuntu, and run XP in a virtual machine such as VirtualBox.

---

