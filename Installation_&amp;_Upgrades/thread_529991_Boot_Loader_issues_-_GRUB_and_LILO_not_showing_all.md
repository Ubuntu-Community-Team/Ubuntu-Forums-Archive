---
title: "Boot Loader issues - GRUB and LILO not showing all installed distros."
date: 2007-08-19
forum: Installation &amp; Upgrades
---

### Post by Bart_D on 2007-08-19
I installed Xubuntu and THEN Zenwalk.  Now, the Xubuntu install went fine and the system was up and running..but after installing Zenwalk, the Zenwalk bootloader DOES NOT show Xubuntu?  I know it's installed...I went into GParted and set a Flag to Boot for the ext3 partition to which Xubuntu was installed?

Am I missing something?

And if I format the partition and reinstall Xubuntu, how would I get rid of the Ubuntu bootloader and use the Zenwalk one (showing both distros).

I know for Windows XP, it showed XP and Zenwalk...why not for Xubuntu?

---

### Post by Pumalite on 2007-08-19
Zenwalk overwrote the MBR. Re-install Grub following these guidelines: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Or use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Bart_D on 2007-08-19
Thanks, I appreciate it.

Now, if I would like to keep the LILO bootloader, is there some modification that I could make....I'd preferto use Zenwalk's LILO bootloader rather than GRUB's.

---

