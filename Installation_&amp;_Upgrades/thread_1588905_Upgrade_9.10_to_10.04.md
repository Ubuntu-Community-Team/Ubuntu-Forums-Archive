---
title: "Upgrade 9.10 to 10.04"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by Garrett85 on 2010-10-05
I recently upgraded my Ubuntu from 9.10 to 10.04 and now it's messed up  my Windows Vista partition. When I try to load Windows it boots to a  strange login menu with low resolution. It then takes me to a screen  with options like Repair/Fix, Recovery, Complete Recovery... I'll click  Repair and and then it will say No errors found, Shut down, Restart.  Please help, thanks. And if all you're going to say is "why are you  using Windows at all anyway", please don't leave a response at all.

---

### Post by efflandt on 2010-10-05
You did not say if you can still boot Ubuntu.

It should not touch anything in Windows unless it is a Wubi installation.  And from what I hear, doing distribution upgrades on a Wubi installation is NOT recommended (there have been issues).

I just updated one system from 9.10 to 10.04 last weekend and everything went smoothly except that ubuntu-restricted-extras went awol, so I had to install that, and flashplugin-installer which appeared to be installed was non-functional until I selected to "reinstall" it.  It was originally 9.04 upgraded to 9.10 because I discovered Ubuntu a week before 9.10 was released.  But it is on a separate partition, so none of the upgrades interfered with booting WinXP Home.

---

### Post by oldfred on 2010-10-06
If grub boots you to windows repair then it  is a windows problem. They say the auto repair only works it you run it three times and then it will overwrite the MBR and you will have to reinstall grub2.

Repair often does not work, some say run 3 times others recommend the command line bootrec.exe
Always run chkdsk and run again until there are no errors, that may be all that is required

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

---

