---
title: "I don't want to say goodbye but it almost ruined me,... help"
date: 2006-10-25
forum: Installation &amp; Upgrades
---

### Post by LinuxLogan on 2006-10-25
Well everytime i install or try to it stops somewhere before it even starts and tells me that i have some error in a fat16 partition and that is can't install.  but then it has already ruined my boot up (which is dual to XP and Linux) and i get an error that is GRUB error.  And I can't boot into anything.

So I have to reinstall Centos Linux or Freespire to get a normal boot menu again.  When i run Ubuntu off of the cd it works flawless... my dispaly, sound and wireless nic all work so i really want this version to work.

any ideas will greatly help me.

thanks
](*,)

---

### Post by orb9220 on 2006-10-25
> i have some error in a fat16 partition and that is can't install. 

You are not trying to install to fat partition are you?

You have to install to ext3 partition which is created in the partitioning part of the install.

You have to have at least 5gb prefered is >10gb partition for / which is root and a linux-swap partition that is twice the size of yer ram.

---

### Post by taurus on 2006-10-25
Install Ubuntu on FAT32 is a real bad idea.  If you want to share files between Windows and Ubuntu, then create an empty partition and format it as FAT32.  It works best that way and many people here have done that so that should be the way to go if you want to install Ubuntu on your machine, dual-booting with Windows...

---

### Post by wkulecz on 2006-10-25
There is an ext2/3 filesystem driver for Windows you can install if you need to access Linux files from windows.  Use the search.

Mounting FAT filesystes in Linux works great too.  No need to install to FAT.  Read-only ntfs access is pretty solid -- Ubuntu could read media files off my Vista RC2 partition. I didn't try write access.

--wally.

---

