---
title: "Tri-Boot problem Fake-Raid Sager 9262 Laptop"
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by pfarrell77 on 2008-01-17
Hello,

Disclaimer - total Linux newb, long time MS Geek with decent residual DOS knowledge (it's all coming back to me, sort of!). 

I'm trying to tri-boot XP, Vista, and Ubuntu 7.10 on my new Sager 9262 Laptop.  My configuration is 2x HDDs in RAID0 using the Intel Fake-Raid.  I then have a 3rd HDD that is not part of the RAID array.

I installed XP, then Vista on the RAID0 with no problems.  I then installed Ubuntu 7.10 on the 3rd HDD with no problems.

My problem is that GRUB only sees the 3rd HDD.  My only options on boot are Ubuntu 7.10, Safe Mode, or Mem Test.  Also, when in the OS, Clicking on Places, Computer, shows only 1 of the 2 HDDs in the RAID array (space wise).  If I click on it, I get an error saying it can't mount it, likely because of the Fake-RAID.

I've attempted to use dmraid and get

user@user-laptop:~$ sudo dmraid -ay
RAID set "isw_cicjfhbjfa_Volume0" already active
RAID set "isw_cicjfhbjfa_Volume01" already active
RAID set "isw_cicjfhbjfa_Volume02" already active

I honestly don't know if that's just showing the 3 partitions Ubuntu created on my 3rd disk or if it's actually seeing all 3 of my disks.

user@user-laptop:~$ sudo dmraid -r
/dev/sda: isw, "isw_cicjfhbjfa", GROUP, ok, 312581806 sectors, data@ 0
/dev/sdc: isw, "isw_cicjfhbjfa", GROUP, ok, 312581806 sectors, data@ 0

I think that's showing my RAID disks because I did have them mounted in positions 1 and 3 (which I'm guessing correspond to sda and sdc) and my 3rd disk is actually in position 2.  I don't know what to do with that info, however.

Finally, in an act of desperation, I booted off the Vista disk and clicked on repair a boot problem.  It reported that the boot loader was fine, along with everything else, but I still only get GRUB and can only get into Ubuntu.

Anyway, I don't know what else to do here to either update GRUB so it sees the RAID array and offers me the options of what to boot into (ideal solution) or undo what I've done with Ubuntu so I can use XP and Vista again (have work software that I need to run under MS) and try this again in the future when fake-raid is better supported.  

Any and all help will be greatly appreciated!

---

### Post by pfarrell77 on 2008-01-18
Figured it out.  Searched for "example grub" and copied someone else's XP entry.  Guessed that my RAID array was mapped to disk 0,0 since it was in position one, and it worked.  Brings up Vista bootloader and all is well.

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda
title        Microsoft Windows XP Home Edition
root        (hd0,0)
chainloader    +1

---

### Post by zeddock on 2008-02-19
I also, just bought a 9262.

So far I have an error in boot, (which I think is from the Splash bug,) and I cannot get my webcamera to work.

I am loaded onto Ubuntu 7.10 32bit, to avoid the limited drivers available for this machine and apps.

Have you found a good support area for Ubuntu on your 9262 yet?

TIA
zeddock

---

