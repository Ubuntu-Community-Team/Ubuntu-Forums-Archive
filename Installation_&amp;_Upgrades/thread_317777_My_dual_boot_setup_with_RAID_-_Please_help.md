---
title: "My dual boot setup with RAID - Please help"
date: 2006-12-12
forum: Installation &amp; Upgrades
---

### Post by LikwidCirkel on 2006-12-12
First post here.  I've been wanting to move to Ubuntu for some time, but haven't had the time until recently.  I want to set up a dual boot system because I can't yet fully give up Windows.


I have some issues to work out...

I have one IDE 160Gb Hdd, and two 300Gb SATA drives.  My SATA/BiosRaid controller is a SIS 180/181 (cheap-o).

I'm a paranoid freak, and I don't want to lose data, so that's why the RAID1.  Having redundancy on all my important stuff will give me peace of mind.  I've heard rumors that if you use fakeRaid and then split the drives, or your mobo dies, then you need the same chipset to access the drives.  I don't have this problem.

What I want is a large chunk of hard drive to be /home and also share space for Linux and Windows(using [this](http://www.fs-driver.org/index.html)).  I also would really like to keep the operating systems on separate drives so that I don't have to deal with GRUB getting wrecked by Windows, and other issues that always seem to happen to me when I set up dual-boot from one drive.  I can easily select which drive to boot from with startup hotkeys, so I much prefer that method.

The problem:

At first I didn't know about fakeRaid, and just assumed that I could install Ubuntu right onto the RAID drives.  I now know that's not easily possible.  I've checked into the RakeRaidEdgy and the FakeRaidHowTo guides on here.  Upon trying the steps on FakeRaidEdgy, dmraid reported "no raid drives" when I tried to use it.  Upon further checking, it seems that my crappy SIS Bios Raid controller is not supported by dmraid. 

Possible Setup options:

1)  Install Linux and Windows on the single IDE drive with a typical dual boot.  Use the other drives as /home and sharespace for both.

Disadvantages:
	- lose out on the speed increases for booting and loading that SATA RAID will give.
	- have to deal with Windows periodically eating the grub boot sector as always happens for me

Questions/Issues:
	- dmraid doesn't support my controller.  If I use Linux softraid on the same drives with Windows fake SIS Raid, will it cause problems?  No operating system will be on the RAID drives.

2)  Install Linux on the RAID drives with a softRAID setup.  This might not work well with Windows BIOS raid, although windows is not installed on that drive; it only needs to access the RAID drives.  Just like option 1), I don't know if this is safe, or will even work.

3) Get some new hardware that will let me do something better.  I am a cheap student right now, so I'd rather not, but I'd consider it.  What would be the best to buy, short of a real hard raid controller?  I think probably just a mobo with rakeraid supported by dmraid.


My main question is, can linux softraid and windows fakeraid be used on the same set of drives, provided that no OS is on them?  How about if only Linux is on the raid drives?

Any workarounds or other suggestions would be appreciated.
I can understand console stuff or editing text files or whatever.

Know of any cheap motherboards for a P4 LGA775?

---

### Post by gn2 on 2006-12-13
What about running virtual Ubuntu PC with VMWare or Parallels within Windows, will that work with RAID?

---

### Post by psusi on 2006-12-15
If you want to access the disks in Ubuntu without dmraid, you have to disable the bios raid support and split the two disks up and use them like they were just two regular disks.  You can partition the disks up so that part is used for a linux software raid, and part is used for a windows software raid, but unfortunately, they can't see each other's style of raid.  

Might I also suggest that you sign up for the ataraid mailing list and supply the devs with information from your raid disks that they can reverse engineer and try to add support for it?

---

