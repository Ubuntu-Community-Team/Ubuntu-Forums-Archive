---
title: "Failure to boot after several reboots on a dual install with Windows 7"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Licargon on 2010-10-13
All right, the situation:

New laptop (Dell Studio 15 -> Intel I5, 4GB DDR3 Ram, Ati HD5470, ...) with Windows 7, and as I need Gcc for my C++ classes at my university, I wanted to dual boot Linux (Virtual is an option, but having it "native" will sometimes "force" me to learn to use Linux, so...)

So I create a seperate partition, install Ubuntu, use Startupmanager to set Windows 7 to default, I reboot, Windows starts, all is well. I reboot: Error: "Operating System Missing".

So I reinstall the Windows 7 MBR, and thus I have to install Ubuntu all over again because that partition is "unfindable". Reinstall works, everything works, I use startup manager again, an hour later after a reboot: The black screen + blinking white cursor error. So I fix the windows MBR YET AGAIN, and it works again.

Try number 3: Same as try number 2

So the problem: Every time I dual boot, the MBR gets screwed, I have to use the windows recovery disk to restore it, and I "lose" the Linux partition...

Anyone else had this problem? I seriously want to double boot 7 / Ubuntu, but with these errors it's plain impossible, as the MBR keeps on getting messed up.

Any ideas on this?

Thanks

---

### Post by wilee-nilee on 2010-10-13
Boot into windows and look for dell data safe.
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)

You can just reload the grub bootloader to the mbr like you did with the MS bootloader. If it is grub2 here is a link. You would do this after removing the dell data safe if that is the problem.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

You can also post the bootscript in my signature if you are still having problems. Post it in code tags as described if you can.

---

