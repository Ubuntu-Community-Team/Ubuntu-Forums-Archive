---
title: "GRUB was never written to MBR, can I do it manually?"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by oskar.hermansson on 2006-06-02
Hello!

After installning Ubuntu 6.06 from the live cd, it seems as grub was never updated or at least its broken now, because when i boot there is never a list of systems to chose from, instead the interactive grub shell is loaded. With the previous text-based installer (like with breezy) i was always asked if I wanted to write grub to MBR. It also recognized my win xp partition which is nice.

I could have missed it, but I think the live cd installer never asked me to write grub to MBR. Can I do it manually?

On the other hand, if I did miss it, in what step does the installer ask if grub should be written to MBR?

I also have the alternate version available, if there is any tool which can be used from that cd.

Grateful for any help

Cheers!

---

### Post by Herman on 2006-06-02
The [GAG Boot Manager]("http://gag.sourceforge.net/") is great for people who want to install new Linux systems or update existing ones because if the bootloader fails for some reason it provides a second way to boot Windows. It provides a second way to boot Linux systems too, if Lilo is installed to the boot block of the Linux (Ubuntu) partition. Doing so will not erase Grub. You can have both installed at the same time.
Here's my web page for GAG: [http://users.bigpond.net.au/hermanzone/p12.htm]("http://users.bigpond.net.au/hermanzone/p12.htm")

Once you can boot again (I hope), you will be happier and able to sort out your Grub problems in a more relaxed mood, at your leisure. 
>  I also have the alternate version available, if there is any tool which can be used from that cd.
 I am not sure yet, I am about to begin exploring the new alternate CD myself shortly...You should be able to. The traditional way to restore Grub with 'Breezy' and earlier releases could do that. There are quite a few different ways following here:
        From the Official Ubuntu Wiki: [Re-installing GRUB ]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28MBR%29")   |     [  Swiss2K thread]("http://www.ubuntuforums.org/showthread.php?t=114332")    |     [Arnieboy thread]("http://ubuntuforums.org/showthread.php?t=76652")   [vnbuddy2002 thread]("http://www.ubuntuforums.org/showthread.php?t=24113")
I hope something here is helpful to you, Regards, Herman :D

---

