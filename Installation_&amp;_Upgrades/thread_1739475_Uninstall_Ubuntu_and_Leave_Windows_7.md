---
title: "Uninstall Ubuntu and Leave Windows 7"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by amithoward on 2011-04-26
Hey everyone,

I have a Dell n5010 which came with Windows 7 pre-installed. I used the built in disk management to divide the C:/ drive into two parts. Using the new free space to install ubuntu.

Unfortunately the battery backup on Ubuntu is extremely low compared to Windows 7. I already have an open thread on that issue so all suggestions are welcome (here is the link to it - [http://ubuntuforums.org/showthread.php?t=1733767]("http://ubuntuforums.org/showthread.php?t=1733767") ).

But until that thing is solved... I want to uninstall Ubuntu. My concern is that if I just format the Ubuntu partition using Windows disk management I'm gonna lose the grub loader and I won't be able to boot into Windows 7 again. I know it's probably a simple thing to do but I've lost a lot of data when I tried to do the same a few months ago on another machine. So I wanna do it the right way this time.

Thanks in advance. ;)

---

### Post by Quackers on 2011-04-26
One option would be to just not use Ubuntu until a fix is found for your problem.
If you want to completely erase Ubuntu and grub you will need to replace grub with the Windows bootloader (to the mbr of the drive). This is done with a Windows repair disc or installation disc. If you don't have a repair disc you should make one now.
In Windows go to Control Panel > Backup & Restore Centre and then in the left pane click on "make a recovery cd". Pop a cd into the drive and you're done in a minute.
Note that this is more commonly called a repair disc. It does not have recovery ability, just repairs.

---

### Post by wilee-nilee on 2011-04-26
Make a recovery disc and follow these instructions and notice the W7 forums link for a visual aid. This reloads the MS bootloader in the mbr, no more grub. You can do what you want with Ubuntu then.
1) Boot with your Vista/Windows 7 recovery or installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Here is a tutorial for making a recovery disc.
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

If there is a problem making a recovery you can download one.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

I feel personally that restoring the actual bootloader for windows=MS first is better then removing Ubuntu and grub then restoring it.

Pretty much the same instructions as the post above I see after posting.

---

