---
title: "How do i boot ubuntu"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by al-qarni on 2011-06-08
I installed Ubuntu 11.04 on a separate partition, with Grub being in it own partition. When I start the PC  only windows Xp is available. So how do I get grub or Ubuntu load with windows xp boot loader?

I tried with Live cd, the sudo grub but then it says command not found. I think its because Ubuntu 11.04 uses grub 2. Is there anyway I can fix this? 

Thank you

---

### Post by oldfred on 2011-06-08
The windows boot loader does not boot Ubuntu. You really need to use grub2's boot loader as it gives a choice of what to boot. There are some very complicated work arounds but I do not know them well enough and they are not easy to implement.

So we can see what is installed where:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

