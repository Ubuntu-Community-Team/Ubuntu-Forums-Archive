---
title: "I NEED HELP! I can't get Windows/Ubuntu dual boot to work!"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by nightmareci on 2006-12-10
I've been trying to find a way to get Windows and Ubuntu installed on my two-hard drive system for a VERY long time now (seems like it's been a year of trial and error) but I have never figured out a way to guarantee a way in which I can have both OS's installed, each on their own hard drive, and having both bootable from the GRUB menu, and having GRUB installed on the drive containing Ubuntu. Today, I had installed and set up Windows, and it was bootable and functional, but after installing Ubuntu, Windows isn't bootable by any of the ways I've tried, but Ubuntu is, although initially the automatic settings for GRUB didn't allow Ubuntu to boot, so I had to edit which drive would be used for Ubuntu.

I don't really know what I should tell you about the setup, but to start, Windows is on my master drive, and Ubuntu is on my slave drive, and I installed GRUB to the slave drive. I thought that Ubuntu wouldn't touch the boot stuff on the master Windows drive, but apparently it did, and now I can't even boot the drive when the slave Ubuntu drive is unplugged. If necessary, I can deal with totally reinstalling from scratch AGAIN, if I have to.

PLEASE help me, I really am sick and tired of this system refusing to work how I want it to, and would like to just get this done and over with. And no "why use Windows?" stuff, I truly need it for a few purposes, as does some of my family members. And I need Ubuntu because, well, it's just plain great for most things I do, especially programming, and it operates more efficiently than Windows does for tasks and some specific games.

---

### Post by confused57 on 2006-12-10
You might want to consider this as an option:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

First, you might want to restore the Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

When you're able to boot the Windows drive, you can set up your system, as described in the first link.

---

### Post by nightmareci on 2006-12-11
I've read about the fixmbr trick with a Windows drive with a broken MBR, but I would like to know if there is a way to just totally reinstall (that the right term?) GRUB and the MBR onto my slave Ubuntu drive, not reinstall Ubuntu, in case things are really weird/broken.

I ask this because my current boot setup is like this: The computer must be set to boot from the master Windows drive, but GRUB is contained on my slave Ubuntu drive, so it goes to that drive's GRUB and then the GRUB menu comes up, then I can select Ubuntu to boot, but of course Windows doesn't boot at all. Also what's weird is I had to set in the boot menu for Ubuntu to boot as (hd0,0), instead of what it was by default as (hd1,0).

The system fails to boot if the slave Ubuntu drive is set to boot first, but this is what I want to do, have all the special GRUB/boot info on the slave Ubuntu drive, and have Windows completely boot-independent (with it's regular NTLDR boot loader, chain loaded into from GRUB) of the slave Ubuntu drive (I want this so I can just rip out my slave Ubuntu drive and have everything still function on the Windows drive, because the slave Ubuntu hard drive is actually mine, but the other drive is my Mom's).

I don't want to take any risks right now, and waste more time trying to get this all working, so I sincerely thank anyone who helps me on this question!

---

### Post by confused57 on 2006-12-11
You might try a Windows entry in your menu.lst similar to this(taken from the first link in my other reply):

```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```

Here's how to (re)install grub, using the Live CD:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Add: Sounds like grub was installed to the Windows mbr, which is why your system won't boot when the slave drive with Ubuntu is removed.  In order to have the Windows drive boot independently(without the Ubuntu drive connected), you're going to have to restore the Windows mbr(see the 2nd link I gave you in my first reply).  Once you're able to repair and boot the Windows drive, you can install grub(using the live cd) to the Ubuntu drive's mbr, then add an entry to boot the Window's drive.
This site has some excellent info on how grub works:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by nightmareci on 2006-12-11
Thank you man, I REALLY appreciate the help! But before I go ahead and do this, should I unplug the slave Ubuntu drive before I do fixmbr on the master Windows drive? I don't want to have fixmbr ruin the slave Ubuntu drive in the process of operating on the master Windows drive, although (re)installing GRUB might fix that if it did happen.

In other words, would fixmbr touch more than one hard drive at all, or would it just touch the one master Windows drive while the slave Ubuntu drive is plugged in, and leave the slave Ubuntu drive alone? Again, trying to avoid any and all possible risks.

Edit:
Can you confirm for me that installing GRUB from the Ubuntu alternate disc would allow me to have a working GRUB alongside my existing non-alternate, Desktop, install? From the information at the "Illustrated Dual Boot Site" (lower link you provided, it's .au or something) it appears that using the alternate disc would be the best way to go if I wanted to (re)install GRUB onto my slave Ubuntu drive.

I won't actually get to working on fixing my system to be how I want it for at least a week or more, so go ahead and take your time to get the best answer for me. And again, I'm very thankful for your support!

---

### Post by confused57 on 2006-12-11
Here's what I would do, if it were my system:
1. Go ahead and disconnect your Ubuntu slave drive...boot up with the Windows install cd(not a recovery cd)...press "r" for recovery, then enter **fixmbr** to repair the Windows mbr(if you don't have a Windows install cd, you can use the Win98SE oem boot floppy, as mentioned in the "Uninstall Linux" link).  Hopefully, this will enable you to boot into Windows...once you can boot Windows, then

2. Connect your Ubuntu drive as slave drive, set your bios to boot first to the slave drive...boot up with the live cd and install grub to the Ubuntu drive mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

The find /boot/grub/stage1 "should" show **root (hd0,0)**, if it does then you do **setup (hd0)**, then quit...the live cd method is much easier than using the alternate cd.

Once grub is installed and you can boot Ubuntu, then you can add the Windows entry I gave you earlier to your /boot/grub/menu.lst.

Another possibility is similar to the instructions in this link(given in my first reply):
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
which would mean you  connect the Ubuntu drive as master, Windows as slave, restore grub to the Ubuntu drive mbr(using the live cd), then add the entry to boot Windows.  Make sure to set bios to boot first to the master drive.  You might have to set your root to /dev/hda1 in your /boot/grub/menu.lst kernel line?

I can't guarantee any of this will work, but it'll give you some options to consider in the next week...main concern is to get your Windows drive to boot independently. You may get some easier & better suggestions before you actually do your troubleshooting.
Good luck...

---

### Post by nightmareci on 2007-01-01
I figured out my problems, and have a configuration **exactly** how I want it. I had to find some documentation about certain GRUB settings so that Windows would be chain-bootable from GRUB, but I got it working. The main issue I had was that I had my BIOS settings wrong, with HDD 1 and HDD 2 being used instead of HDD 0 and HDD 1, so I'd boot the wrong disk when I intended to boot one of the disks.

It's very nice to have a special configuration like this, because Windows is entirely independent of Ubuntu, as is Ubuntu independent of Windows, so I needn't worry about pulling one of the hard drives out, which I'll have to do when I move out/go to college.

I sincerely thank you for your assistance, but the only thing that I really needed was knowing how to use fixmbr on the Windows disk so that it'd be bootable, otherwise all the software was installed just fine.

---

### Post by gn2 on 2007-01-01
> **nightmareci said:**
> I figured out my problems, and have a configuration **exactly** how I want it. I had to find some documentation about certain GRUB settings so that Windows would be chain-bootable from GRUB, but I got it working. The main issue I had was that I had my BIOS settings wrong, with HDD 1 and HDD 2 being used instead of HDD 0 and HDD 1, so I'd boot the wrong disk when I intended to boot one of the disks.

It's very nice to have a special configuration like this, because Windows is entirely independent of Ubuntu, as is Ubuntu independent of Windows, so I needn't worry about pulling one of the hard drives out, which I'll have to do when I move out/go to college.

I sincerely thank you for your assistance, but the only thing that I really needed was knowing how to use fixmbr on the Windows disk so that it'd be bootable, otherwise all the software was installed just fine.

Glad you're sorted, I had similar problems once and wrote the guide in this link once I had it figured out: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

