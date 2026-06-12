---
title: "Problem with dual boot Windows 8 with Ubuntu 16"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by brelf on 2017-11-05
Hey! I am having this problem for quite a while and I am not sure why, I hope i can find it out here! :D

So I have installed ubuntu alongside my windows 8 computer (A DELL Vostro 5470 A-30), and everything got working well until suddenly one day the windows stopped working. I am not sure if it was due to an update/upgrade of my ubuntu, because both used to work normally. I don't know if it as boot problem also. I have installed ubuntu at the 14 version and upgraded it until the 16 version.

So my currently, when I try to run windows from my GRUB I get this black screen: [https://i.stack.imgur.com/mh8sN.jpg](https://i.stack.imgur.com/mh8sN.jpg)

EDIT: Before it stopped working it worked with the black screen at the start, and then regular windows (after I installed the dual boot). I don't know if the black screen is or isn't the actual problem.

And it keeps on that screen until it restart by himself. After trying 3 times, the system repair automatically start, I tried all the repairs (restarting, restoring, ...). However many simply do not work while others I can't even start (poor windows). I tried some commands on prompt such as "scannow" or "bootxxx" or "chkdisk" and nothing worked (Also tried on live USB with windows). Here is a photo of my partitions (I don't know if the problem can be on that too): [https://i.stack.imgur.com/QPf4M.png](https://i.stack.imgur.com/QPf4M.png)

I have no idea what can be happening or how to discover and fix it. Thanks!

---

### Post by ubfan1 on 2017-11-05
To summarize for others:  You have a legacy Windows 8 install on an MSDOS partitioned disk.  No UEFI involved.  The screen looks like some common video problems, but if you are seeing grub, and it's just Windows with the problem, and Ubuntu runs OK, that's a new combination.

---

### Post by oldfred on 2017-11-05
Windows 8 & 10 often update in back ground unless you change settings.
And updates may turn fast start up back on which is just hibernation.

But grub does not boot hibernated Windows.
You may need your Windows repair flash drive or installer with the recovery/repair console (f8).

Or  you may need to temporarily reinstall a Windows BIOS boot loader to directly boot Windows & turn off the fast start up.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

       
 How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by brelf on 2017-11-05
Hello! I tried this links:
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) 
[https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](https://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)

running REG ADD "HKLM\SYSTEM\CurrentControlSet\Control\Session Manager\Power" /V  HiberbootEnabled /T REG_dWORD /D 0 /F
and /fixboot and /fixmbr

I think the Fast Start Up was already turned off, beacuse after running this command, nothing happened (I tried HiberbootDisabled to see what would happen and I had to reinstall grub e.e. Everything in ubuntu is still working, the problem is with the windows partition). So my guess is that Fast Start Up was already off. So I think we still don't know what is happening (Or I didn't understood) :S
Anyway, Thanks!!!

---

