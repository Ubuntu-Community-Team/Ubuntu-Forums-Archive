---
title: "Problem with all Linux installations"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by mjmikelson on 2008-08-16
Hi, thanks for your help.  I've got a group of 6 old computers I'm trying to install Linux on.  I try all variants of ubuntu from 5.04 to 8.04, and I have varying degrees of success, but they all fail. For example, I have an old super micro P6DGU/DBU board with 512 MB RAM, a 30gb IDE drive, and 3 18GB SCSCI's on it.  I had Ubuntu Server 8.04 on it running just fine, then I took the machine to a friend's house to do some work.  When I got there, it didn't see the IDE drive.  Ok, so I go home with it, and try to reinstall.  Nothing doing...I change out the hard drive, to a brand new IDE 160 gb HD (maxtor) and I get squashfs error, and I/O errors where it sees the hard drive, but says that this sector can't be installed.  So, I move the hard drive to an HP Vectra VL420 (P4, 1.8ghz 1gb pc133 RAM) and get the same thing.  

Then, I try on my 4 Compaq Deskpro EN933's....same issue.  I swap hard drives around in a methodical fashion....same result.  I try installing Mepis Linux, VMWare ESX Server, and Open SUSE 11.0, all have varying degrees of the same issue.  I get the Live disks with all but the Ubuntu 8.04 (downloaded and burned at 2x,4x, and 16x), yet can get the live disk to run with 6.10 (official disk I got in the mail).  

I try three different hard drives in all machines....all have the same error.  I try to install Windows 2000 Advanced Server on it, no problems.  Works fine, sees the computer and installs perfectly.  These computers all hiccup only with Linux.  The Ubuntu live disks either start and hang up at varying degrees of installation (or won't start installation at all), and all Linux distro's don't install properly and have the "squash fs error, unable to read page, block ...." and the  "buffer I/O error on device sr1, logical block XXXX"  

I can't even get the live CD's to work on these boxes, other than Knoppix....which works fine.  Here's the kicker....if I install VMWare server (free edition) within Windows Server or XP Pro...I can get all of the linux distros's to work fine. 

But....as I noted, I had Ubuntu Server working fine on the Super Micro, and I had Ubuntu Desktop 8.04 it dual booting with XP  Pro on the VL420, meaning the hardware hasn't changed.  

Any thoughts would be appreciated!

Thanks!

---

### Post by Vivaldi Gloria on 2008-08-16
I don't know anything about your computers but here is a standard list of things to try in your situation:

**1)** Check the cd you are using:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

and burn it slow.

**2)** Google your computer model and ubuntu. May be there's a fix. Seach launchpad bug reports and ubuntu forums.

**3)** Play with boot options of the ubuntu cd:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

**4)** Try alternate cd.

**5)** Install a cli-only system using the minimal cd:

[http://ubuntuforums.org/showthread.php?t=882596](http://ubuntuforums.org/showthread.php?t=882596)

And then add a desktop environment. For example:

sudo apt-get install ubuntu-desktop.


If nothing works file a bug report.

---

### Post by tfosorcim on 2008-08-16
May be a problem with the CD drives not reading burned disc.

---

