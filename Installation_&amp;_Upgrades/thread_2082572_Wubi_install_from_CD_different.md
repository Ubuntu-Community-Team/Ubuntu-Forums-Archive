---
title: "Wubi install from CD different?"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by er86 on 2012-11-09
So I have used Wubi for ages as I still need Windows.  I recommend it to everyone who wants to dabble since if they do not like it they can just use Add/Remove Programs to get rid of it.  So I was a bit surprised when I gave someone a CD and they tried to use it to install Ubuntu and ended up with a complete mess.  I duplicated things myself so they did not do anything wrong.  I am confused...

Why doesn't the wubi on the CD behave the same as the one you can download?  If you try to launch it it opens a window that gives you the buttons "Demo and full installation" and "Learn more" instead of what I expect to see - i.e. a Windows program being installed.  If you follow the prompts and reboot it will slice and dice your hard drive.  To a knowledgeable person there are hints this is happening, but when I tell people they can use Wubi and not risk messing anything up, how can they be blamed for just clicking since it says you can use it along side windows.  GRUB gets installed in a traditional dual boot setup if you use the CD.  How is a novice supposed to know this?  Why on earth is there a wubi app in the root directory of the CD?

How can I suggest Ubuntu going forward where someone doesn't have to download the silly installation when a CD is a LOT less expensive with time and bandwidth charges?

Ubuntu 12.04.01 (LTS)

---

### Post by critin on 2012-11-09
If it's used with the installer shown on this wiki page, it's easier.  It can be done with wubi exe., but you kinda have to know how.  The installer is safer.

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by Frogs Hair on 2012-11-09
The ISO is the same size whether it is downloaded using Wubi .exe or from the Ubuntu download mirror. I have friends who have used my Ubuntu disk to install via Wubi in the past. It installs much faster because the needed packages are included with the disk and don't need to be downloaded. 

If you use Wubi from a 12.04 disk it will install 12.04 and if you use Wubi from the web site it installs the current version.

---

### Post by bcbc on 2012-11-09
Things are in transition with Wubi. From 12.04 they disabled it from installing from the CD. Ostensibly to allow it to be updated separately (outside of the release cycle).

So running the same wubi.exe on a folder on your computer will allow you to install inside your windows, but when run from CD will only offer to 'restart and install from CD' or use the 'cd boot helper' (which is a wubi way of booting from CD).

So, for 12.04 the answer is to use the --force-wubi option and then it will act the same, even from a CD. I think it works the same on 12.10.

But I believe they are removing wubi.exe from the ISOs for 13.04. And there's even talk of completely rewriting wubi for 13.04.

---

