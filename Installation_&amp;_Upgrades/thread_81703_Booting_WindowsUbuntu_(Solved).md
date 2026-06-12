---
title: "Booting Windows/Ubuntu (Solved)"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by BFP on 2005-10-25
In a recent fit of geekery, I decided to give Ubuntu a try. So, I installed it from the CD to a spare hard drive, while keeping XP on my main drive, hoping to work with them both while I give Linux a try.

Linux seems to have installed successfully, and Windows still works, but I can't boot normally to either of them. If I boot to the Windows installer disk, I can load either OS with no problems, and they both seem to work, but without the disk I just get "Error 17" when trying to boot.

I assume I need to fix the Master Boot Record somehow. If I am right, what is the best way to go about this?

EDIT: Following advice from elsewhere, I ran the System Recovery Console and rewrote the MBR. I now boot normally to Windows. What do I need to do to be able to boot to either OS?

---

### Post by landotter on 2005-10-25
Search the forums for "restore MBR" and you'll find half a dozen solutions I don't feel like getting carpal tunnel over. :P

---

### Post by aysiu on 2005-10-25
[QUOTE=landotter]Search the forums for "restore MBR" and you'll find half a dozen solutions I don't feel like getting carpal tunnel over. :P[/QUOTE] Don't bother searching. Here it is: [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

---

### Post by BFP on 2005-10-25
You are my sunshine.

---

### Post by landotter on 2005-10-25
[quote=aysiu]Don't bother searching. Here it is: [http://ubuntuforums.org/showthread.php?t=24113]("http://ubuntuforums.org/showthread.php?t=24113")[/quote]

Just trying to teach a guy to fish...

:cool::lol:

---

### Post by BFP on 2005-10-25
In future, I'll spend a little time more using the search functions for the forum. Thanks to everybody for this advice. I'm going through this process now.

After going through the process to restore GRUB, the system now displays 'Error 17' during a boot, and I am able to boot into neither system. By booting with the windows setup disk, I get the option to boot either into Ubuntu or Windows XP.

This option is apparently what GRUB is when it successfully loads. I am able to use either OS properly with no problems. However, without first booting from the setup CD for windows, I am unable to boot to either system. 

What do I need to do?

---

### Post by SlrWebDesign on 2005-10-25
I get the same error yesterday (Error 17). It happends after a change in the drive boot sequence. I needed to reinstall grub. Be carefull to reinstall the windows Boot Loader in the windows partition, not on the MBR.

---

### Post by BoxCar on 2005-11-19
I'm having the same problem. Grub won't load unless I have the WinXP cd in the drive.

When the XP cd is in the drive (it reaches the stage where it says push any key to boot from CD -- i don't, i just let it go to the next stage) and Grub loads. Once this happens i can boot without problem into either OS.

Without the XP cd in the drive, I get an error 17 after stage 1.5 of grub.

Any help would be greatly appreciated.

Edit: Here's some more info about my situation [http://www.ubuntuforums.org/showthread.php?t=92537]("http://www.ubuntuforums.org/showthread.php?t=92537")

---

