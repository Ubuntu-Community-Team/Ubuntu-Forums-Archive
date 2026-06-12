---
title: "Dual Boot.  Can't boot Ubuntu 10.10 anymore."
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by Firedragon1026 on 2012-02-25
On my laptop, I use a dual boot between Ubuntu 10.10 and Windows 7 because unfortunately I need Windows for some software I use for school.  Well, eventually Windows got so corrupt that I needed to re install it (imagine that!).  I borrowed a Windows 7 Ultimate 64 bit disk from a friend and re installed Windows.  I installed in on the same partition Windows was on before.  That went fine, only now I can't get into Ubuntu.  When it boots up, it goes directly into Windows.  It's like it doesn't even know there's another partition on the computer.  I tried re-installing Ubuntu from a disk, but that doesn't seem to work either.  When I try to boot from the Ubuntu install disk, I get as far as the Ubuntu logo and no further.  I sat there for 20 minutes looking at the Ubuntu logo and nothing else happening.  

Can anyone help?  I'm hopelessly lost right now and beyond frustrated.

---

### Post by stinkeye on 2012-02-25
Easiest way  would be boot into a live Ubuntu cd or usb
and install [**_[COLOR="DarkRed"]Boot-Repair[/COLOR]_**]("https://help.ubuntu.com/community/Boot-Repair").

---

### Post by darkod on 2012-02-25
Windows overwrites the grub2 bootloader and of course is not aware of linux OSs and boots directly windows.

There was a simple solution, to reinstall grub2 on the MBR of the disk without much effort.

But you probably made a mistake reinstalling ubuntu once more, you never need to do that if grub2 gets overwritten because your installation is still there. Right now we have no idea what is the current status.

You can try the boot-repair as suggested, you can also try running the boot info script, it's one option that boot-repair offers. You can find the script in the link in my signature also, you can download, run it and post the results as explained there, it will show more details.

During the second ubuntu install unless you selected the manual partitioning and installed over the first installation, you now have 2 ubuntu installations because it never overwrites itself or another OS unless you specifically tell it to.

---

### Post by Firedragon1026 on 2012-02-25
I haven't yet reinstalled Ubuntu.  I made an install disk, but I haven't had much luck using it.  I'll try the boot repair disk and see if that does anything.

---

### Post by stinkeye on 2012-02-25
See this [**_[COLOR="DarkRed"]How to restore the Ubuntu grub bootloader (9.10 and beyond)[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1")
to restore manually from a live cd.

---

### Post by Firedragon1026 on 2012-02-25
The boot repair disk worked perfectly.  Thanks everyone.

---

