---
title: "Trouble Installing with Livecd and USB"
date: 2011-01-08
forum: Installation &amp; Upgrades
---

### Post by iFuzo on 2011-01-08
Well today I decided I wanted to go back to ubuntu but after trying both ways I couldnt do it.

The livecd was giving me an error saying something about partition or livecd being broken and when I would try with the USB it would get stuck on Preparing to install Ubuntu for 25 minutes until I would close it and get the following crash report "Sorry, the program "parted_server" closed unexpectedly".

Does anybody have any idea on how I can install ubuntu trouble free?

Syslog - [http://pastebin.com/raw.php?i=ELmPHiPG](http://pastebin.com/raw.php?i=ELmPHiPG)
Partman - [http://pastebin.com/raw.php?i=3KZFwvt8](http://pastebin.com/raw.php?i=3KZFwvt8)

---

### Post by kev77 on 2011-01-08
try downloading another copy of ubuntu and try again, sometimes errors can occur when downloading. has happened to me in the past. you may also want to try a different version 10.04/10.10!

---

### Post by iFuzo on 2011-01-08
> **kev77 said:**
> try downloading another copy of ubuntu and try again, sometimes errors can occur when downloading. has happened to me in the past. you may also want to try a different version 10.04/10.10!

I have tried redownloading.

---

### Post by theasprint on 2011-01-08
Hi,

To really know if your Ubuntu disc is working, go and check the MD5 sum of the .iso file 

Here's the link: [https://help.ubuntu.com/community/HowToMD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM")


If all comes out alright then your .iso file should be at its best. 
For further precautions, burn the .iso file at the lowest speed into the disc.

---

### Post by iFuzo on 2011-01-08
> **theasprint said:**
> Hi,

To really know if your Ubuntu disc is working, go and check the MD5 sum of the .iso file 

Here's the link: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)


If all comes out alright then your .iso file should be at its best. 
For further precautions, burn the .iso file at the lowest speed into the disc.

I've already burned the ISO to the CD so how do I check it?

I've also added syslog and partman log to main post.

---

### Post by dmoench on 2011-01-08
[FONT=Arial][SIZE=2]I've been having the same problem [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=black]booting off of a USB stick on a new HP Pavilion dm1z laptop/super-netbook (Windows 7 pre-installed, No CD drive). I've been able to test multiple versions[/COLOR] (with varying degree's of smoothness), but none of them have been able to successfully install.[/SIZE][/FONT][FONT=Arial][SIZE=2] I have no desire to dual boot, I want to get rid of Windows 7.

I've tried the following versions, and all have gotten stuck:
[/SIZE][/FONT]
[LIST=1]
[*]
[LIST]
[*][FONT=Arial][SIZE=2]Ubuntu Desktop 10.10[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]Had crashing issues when not plugged in to power.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Installer got stuck at the same[/SIZE][/FONT][FONT=Arial][SIZE=2] "[/SIZE][/FONT][FONT=Arial][SIZE=2]Preparing to install Ubuntu" step. (Don't remember if there was an error message)
[/SIZE][/FONT]
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST]
[*][FONT=Arial][SIZE=2]Xubuntu Desktop 10.04[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]No crashing issues.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Installer got stuck and could not go beyond the keyboard layout step (error message popped up- Sorry, the program "parted_server" closed unexpectedly).[/SIZE][/FONT]
[/LIST]
 
[/LIST]
 
[/LIST]
 
[LIST=1]
[*]
[LIST]
[*][FONT=Arial][SIZE=2]Ubuntu Desktop 10.04 LTS[/SIZE][/FONT]
[LIST]
[*][FONT=Arial][SIZE=2]No crashing issues.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Installer got stuck and could not go beyond the keyboard layout step (error message popped up- Sorry, the program "parted_server" closed unexpectedly).[/SIZE][/FONT]
[/LIST]
 
[/LIST]
 
[/LIST]
 [FONT=Arial][SIZE=2]There are a few other threads discussing the same/similar issues, but being a newbie most of what they're talking about is a bit over my head- 
[/SIZE][/FONT]
[LIST]
[*][Stuck With Installation]("http://ubuntuforums.org/showthread.php?t=1629893&page=2")
[*][Trying To Install Ubuntu Maverick...]("http://ubuntuforums.org/showthread.php?t=1592342")
[/LIST]
[FONT=Arial][SIZE=2]Thanks,
David

[/SIZE][/FONT]

---

### Post by k.smith on 2011-04-04
I'm having the very same issues, already tried 10.4 and 10.0 and over diff had disks setups and nothing

---

