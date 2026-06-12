---
title: "Unable to update 12.04"
date: 2017-06-26
forum: Installation &amp; Upgrades
---

### Post by sachi89 on 2017-06-26
Hi,
I've been trying to update my laptop which has got Ubuntu 12.10-quantal.It has no CDROM and USB ports are out(due to which i'm kind of struggling to upgrade the version).

From few of the posts, came to know that its EOL and cannot upgrade directly to latest LTS version.Can someone help me out?Appreciate it.

I have tried almost all the initial work aorunds and sources.But could not get it to work.
[I]sudo apt-get update

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/quantal-updates/multiverse/binary-i386/Packages  404  Not Found [Mirror: [http://archive.ubuntu.com/ubuntu/]](http://archive.ubuntu.com/ubuntu/])

W: Failed to fetch mirror://mirrors.ubuntu.com/mirrors.txt/dists/quantal-updates/restricted/binary-i386/Packages  404  Not Found [Mirror: [http://archive.ubuntu.com/ubuntu/]](http://archive.ubuntu.com/ubuntu/])

E: Some index files failed to download. They have been ignored, or old ones used instead.
[/I]


[I]
 do-release-upgrade
Checking for a new Ubuntu release
No new release found
[/I]

---

### Post by howefield on 2017-06-26
This page might help you get an upgrade going : [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

My recommendation would be to get a fresh install however that might be, eg using a monitor with integrated USB slot or some other such device ?

---

### Post by Bucky Ball on 2017-06-26
> **howefield said:**
> My recommendation would be to get a fresh install however that might be, eg using a monitor with integrated USB slot or some other such device ?

+1 to this. Simplest and easiest. 12.10 been EOL for years so might be hard to kickstart and, even if you do manage to, may end up with a mess.

16.04 LTS is the current LTS, supported until 2021. If your old machine has low specs, modern Ubuntu may be a little sluggish. If this is the case, try something lighter like Xubuntu or Lubuntu (LTS of both of these flavours have three years support, until 2019). 

Good luck.

---

### Post by Impavidus on 2017-06-26
The best way is a fresh install. Without dvd drive or working usb ports this gets a bit complicated. I read once that it may be possible to store the .iso file of the live disk on your hard drive and use grub to boot it. Never attempted it myself. You could also take the hard drive out of your computer, attach it to a different computer and use that to install Ubuntu. Then move the hard drive back. Make sure that BIOS/UEFI settings match and don't install proprietary drivers. That may be the easiest way.

---

### Post by CatKiller on 2017-06-26
I would also recommend a fresh install.

Otherwise, you can use the oldreleases approach linked above to get to 14.04 LTS and then to 16.04 LTS. You can go LTS to LTS without doing the steps in between, but if you're on a non-LTS you need to do all the intermediate upgrades till you get to an LTS.

---

### Post by kc1di on 2017-06-26
Hello sachi89 and welcome to Ubuntu,

As others have already pointed out ubuntu 12.10 has been EOL for some time now. 
[here is a thread ]("https://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how")from Ask Ubuntu that may be of help in your situation.

---

### Post by efflandt on 2017-06-28
If you have another computer that you could connect the drive to, you could install it that way. For example, for installing Ubuntu to mSATA of a failed laptop, I used the mSATA in SATA adapter on another laptop to install Ubuntu to the mSATA (so I could do other things on my PC without waiting). Then I installed that mSATA in SATA adapter in my PC as /dev/sdb and it works fine. That was all with older computers that do not have UEFI.

Assuming that your laptop uses legacy BIOS, not UEFI, it would be best to use a computer with legacy BIOS (or UEFI switched to BIOS mode) while installing Ubuntu to the drive. I would not know if there is a way to force BIOS install from UEFI mode. Grub in legacy BIOS mode uses UUID to find partitions, so even if the drive is /dev/sdb or sdc when you install Ubuntu on it, as long as you put grub in the mbr of that drive, you should be able to switch it to your laptop and it should simply boot. It would be best if you temporarily disconnect all other drives during install on a different computer because then you could simply install to entire drive. If you have any other drives connected, you would need to select "Other" during install partition selection (make sure you have correct drive), so you could select to put grub on that drive instead of default to primary drive.

---

### Post by johndough2 on 2017-06-29
Hi

Only the brave...

I think only Plan A applies in this case, and I suggest you go from 12.04 in stages.  Raring, Saucy before jumping to xenial then zesty.

 
 We have a Plan A, B and C.
 
 
 Plan A is to follow the excellent idea of a network cable plugged into your router.  
That way you cannot have WiFi issues.  Also the firmware upgrade may be useful.
 
```
 
 cd /
 sudo apt update
 sudo apt dist-upgrade (it’s a biggie and will take time).
 sudo apt install joe
```

```
 sudo chmod 755 /etc/apt/sources.list
 sudo joe /etc/apt/sources.list
```
 
 
 Change the word trusty, utopic (or whatever your repos are) to "zesty" in a few places.
 
 
```
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial main restricted universe multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) xenial-updates main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) xenial-security main restricted universe multiverse 
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) zesty main restricted universe multiverse
 deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) zesty-updates main restricted universe multiverse
 deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) zesty-security main restricted universe multiverse
```
 
 
 No mouse, so edit with arrow keys for navigation.
 
 
 Ctrl K + X   3 keypress Save and Exit.
 
 
```
 sudo chmod 644 /etc/apt/sources.list
```
 
 
```
 sudo apt update
 sudo apt dist-upgrade
``` (it’s a biggie and will take time). You can always press NO.
 
 
 Plan B use something like “LinuxLive USB Creator” or “CDBurnerXP” and do a fresh install using your current .iso file.

 
 
 Plan C is to go to your local Sainsbury (UK mainly) and buy a Linux Mag  with a cover disk for £6 and you will have a backup.  It might be  something non-mainstream, but derived from Debian.

---

