---
title: "Ubuntu knocks out my boot manager"
date: 2005-01-30
forum: Installation &amp; Upgrades
---

### Post by Kokosnuss on 2005-01-30
Hello Ubuntu comunity,

I'm a complete Linux Newbie and installed Ubuntu on a spare partition today, hiding my Windows XP partition. It all worked fine and I'm very satisfied with the OS, except for the fact that it knocked out my boot mangager and replaced it with "Grub".
"Grub" automatically launches Ubuntu but doesn't give me a possibility to lauch Windows XP.
After reinstalling the boot manger called "Boot Mangager Pro" I was able to boot Windows XP again but on selecting Ubuntu it told me Ubuntu couldn't be found.

Well, "Grub" and "Boot Manager Pro" seem to compete against each other...
Should I try to install Ubuntu again - this time with all partitions made visible? Or will Ubuntu "kill" my XP partition? And will Grub give me a possibility to select which OS I would like to lauch every time I start my computer?

Thanks in advance,

Felix Feustel

---

### Post by crane on 2005-01-30
I'm not understanding how you made a partition "visible"
Did you look at your /boot/grub/menu.lst ?

There should have been something that looked like :

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


That is at the end of the file.

---

### Post by Kokosnuss on 2005-01-31
No, I hid the other Partitions with my boot manager...

My question is now:
"If I installed Ubutu with all partitions set visible, would it detect the other OS (WinXP) and add it to 'Grub'?"

---

### Post by celloandy on 2005-01-31
Grub is a good boot loader, and certainly capable of booting XP... also, since your other boot loader is no longer booting Ubuntu, I doubt that those other partitions are still "hidden," or whatever it was that your other boot loader did, so I'm reasonably sure that Ubuntu is able to see those other partitions.  If you do reinstall Ubuntu, the installer will most likely autodetect the XP partition, and add a grub entry to boot it (it did for me).  Reinstallation isn't really necessary, though... you could pretty easily boot the machine into Linux using a Gnoppix CD or something, and use the grub-install script to put switch back to grub as your boot loader, then manually manipulate your grub.conf file to add an entry for WinXP.  This isn't really *that* hard, though, it requires a little technical know-how with Linux, I guess.  Hehe, maybe it'd be a good learning experience!  Anyway, if that's your cup of tea, consult [http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Multiboot-with-GRUB.html](http://www.ibiblio.org/pub/Linux/docs/HOWTO/other-formats/html_single/Multiboot-with-GRUB.html) or something similar.  If not, reinstalling would work, too.

Andrew

---

### Post by Kokosnuss on 2005-01-31
Hey, thanks a lot, that answers many of my questions for now. I think, I will take the easier way and reinstall Ubuntu...

There is one little question left though...
There are also some Fat 32 partiotions on my hard disk that I'd like to run as shared partitions (Linux-Windows). The partiotion manager during Ubuntu installation offers me to 'mount' these partitions. But where should I mount them to? Should I simply mount them to '\'+partition's name? Or what is the usual way? I remember reading somewhere that I can change these settings later inside Linux. Is this true?

Thanks in advance,

Felix

*sometime later:* 
*I just read that the usual 'mount point' seems to be '/mnt/'+partition's name, correct?*

---

### Post by Buffalo Soldier on 2005-01-31
Yes, you can mount them later. On how to mount FAT / NTFS partition:

[http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)

---

