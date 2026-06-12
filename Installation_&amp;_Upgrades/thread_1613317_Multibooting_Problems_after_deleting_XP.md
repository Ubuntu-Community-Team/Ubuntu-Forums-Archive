---
title: "Multibooting Problems after deleting XP"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by philoid on 2010-11-04
Hi, guys.

I am a new UBUNTU user.
I had installed OS in my computer in the order of XP, Win 7, and finally UBUNTU.
With EasyBCD, I managed multi-booting order of XP and Win7.

That is, after choosing Win7 or UBUNTU from GRUB, 
(If I chose Win 7) I should choose XP or Win 7 to boot.

Using UBUNTU, I think that I do not need XP, so I formatted the hard disk where XP was
installed.

However, after deleting XP, I can not boot Win7 from GRUB, although there is still
menu for Win7.

Could anyone help me to fix this problem? I want to use Win 7 with UBUNTU...

Thank you.

---

### Post by wojox on 2010-11-04
Try reinstalling Grub2 to your MBR. [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

Then you'll boot into Ubuntu, open a terminal and type

```
sudo update-grub
```

It should see Windows 7 then.

---

### Post by oldfred on 2010-11-04
If you installed XP first and that partition was the active partition (boot flag) then all the boot files for win7 were in the XP partition. If your win7 install is in a primary partition it is repairable with a win7 repair CD. If in a logical partition you will have to reinstall or with lots of risk directly edit partition table to convert it to a primary (will depend on where it is)

How windows sets up multibooting - lots of detail but pictures pretty well explain it:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

You have to move boot flag to win7 partition before repairs or it will not see the partition. Also will not see it if logical partition:
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

