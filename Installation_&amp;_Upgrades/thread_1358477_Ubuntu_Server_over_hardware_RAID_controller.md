---
title: "Ubuntu Server over hardware RAID controller"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by n0nc3ntz on 2009-12-18
Good Morning,

I am a linux newbie first and foremost. I am trying to setup a my first LAMP server but I cannot seem to get my installation of sever 9.10 to boot correctly. I set my raid controller to RAID0 stripped but when I run the setup I see that both of my Harddrives are present instead of just one complete volume. I keep on with the install but when I reboot I get this gem.

GRUB loading.
error: no such partition
grub rescue>

I have tried to recover grub via grub-update but after running it I am still not able to reach my install. I tried to use the live disk to download dmraid but when I get to the desktop of the live session I do not see an install icon and the session seems to error out because it is missing some files..... 

Any help would be greatly appreciated. 
Noncentz

---

### Post by darkod on 2009-12-18
Fist of all, do you have hardware raid (with dedicated card) or what is known as fakeraid (onboard BIOS raid)? I'm no server and raid expert but I think it makes a difference.
If you had hardware raid the card itself will create one device from both your striped drives and there is no way ubuntu would see them as separate drives.
For some fakeraid stuff, look here:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

If you have only onboard fakeraid I believe the software raid, or softraid, is much better and preferred option. Look here:
[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

---

### Post by n0nc3ntz on 2009-12-18
darkod,

I am using a hardware raid controller that I just purchased. The board I got didn't come with an onboard RAID controller so I picked one up. 4 port SATA RAID controller PCI card.

---

### Post by darkod on 2009-12-18
> **n0nc3ntz said:**
> darkod,

I am using a hardware raid controller that I just purchased. The board I got didn't come with an onboard RAID controller so I picked one up. 4 port SATA RAID controller PCI card.

Uhh... I guess ubuntu can't recognize it then. Maybe doesn't have the driver, etc. Not sure what to do in this case.

---

### Post by gilson585 on 2009-12-20
Some cheap raid controllers are actually using fakeraid and not real hardware raid. It sounds like to me this may be the case. Using the livecd after installing check gparted to see if it lists your partitions correctly. If so check out my instructions on installing 9.10 on fakeraid [http://ubuntuforums.org/showthread.php?t=1360445](http://ubuntuforums.org/showthread.php?t=1360445)

---

