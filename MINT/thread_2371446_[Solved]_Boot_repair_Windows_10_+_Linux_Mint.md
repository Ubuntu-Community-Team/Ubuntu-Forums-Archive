---
title: "[Solved] Boot repair Windows 10 + Linux Mint"
date: 2017-09-14
forum: MINT
---

### Post by sguivarch on 2017-09-14
After installing Windows 10 on my Asus Laptop, I've got a huge problem, I can't manage to see it on the grub menu, I already tried a lot of things and loose a lot of time, i'll be so glad that someone could help me ! 
(I think it's a problem of MBR/GPT compatibility)
If i ask boot-repair to repair MBR the laptop boot on windows without any grub prompt. If I run boot-repair again, the labtop do not see Windows anymore and grub only propose to boot on Mint (this is the state where i'm now).

Here is my last boot-repair report :

[http://paste.ubuntu.com/25534369/](http://paste.ubuntu.com/25534369/)

Thanks again for your help.

Sébastien

---

### Post by oldfred on 2017-09-14
Moved to Mint sub-forum.

Your installs are BIOS/MBR, but you must have newer UEFI system as you booted live installer/Boot-Repair in UEFI mode.
Best to always boot in same boot mode.

Boot-Repair is telling you problem.
> Windows is hibernated, refused to mount.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by sguivarch on 2017-09-14
Thanks for your answer, i'll try to desactivate the hibernate mode but the problem is that for the moment I can't boot on windows anymore :-(. It's a bit late for me to try something else today, i'll try it later and tell you if I manage to solve the problem. Thanks again !

---

### Post by oldfred on 2017-09-14
One of the advantages of UEFI installs is that you still can boot Windows from UEFI boot menu.

With BIOS/MBR installs, system only boots from the MBR.
Boot-Repair's only Windows fix is to install a generic Windows boot loader to MBR, but if Windows hibernated, then Boot-Repair probably will not even offer to do that.
You need your Windows repair flash drive or installer and its repair console. Or maybe temporarily install Windows boot loader and see if f8 gets you into the internal repair console.
And then reinstall grub after Windows is working.

Grub only boots working Windows. And the new Windows 10 likes to turn fast start up on with many updates. And those updates can be in background so you do not know that then Windows is hibernated & then grub will not boot it.

Another advantage of UEFI installs as then it is easy to directly boot Windows. But since you have BIOS/MBR very difficult to convert. It becomes major backups (which of course you already should have) and total reinstall. How you boot install media UEFI or BIOS is then how it installs.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by sguivarch on 2017-09-15
Hy, this morning I boot my laptop and the Grub menu offer me to boot on Windows or Linux, I haven't done anything more than another grub rescue...I don't understand why but It works ! I'll live it like this for the moment because I need my computer for the work but I asume that one day I should do a new installation with everything in UEFI mode...Thanks again for your help, I'm new in the forum it's really nice to have a such support !

---

### Post by oldfred on 2017-09-15
Glad it is working.

Probably was not the hibernation issue, but something that Boot-Repair may have tweaked?
I would make sure you have Windows repair flash drive or know if Windows installer you have has the Windows repair console as hibernation issue can still come up.

---

