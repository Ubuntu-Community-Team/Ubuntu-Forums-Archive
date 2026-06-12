---
title: "boot repair"
date: 2013-08-08
forum: Installation &amp; Upgrades
---

### Post by nyarlatotheph on 2013-08-08
Dearest all,

I tried to work a couple of days and looked at  a number of former answers, but I am kind of stuck.
I have an Acer5920G (32 bit), double boot Ubuntu 8.04 and Vista. No problems.
I decided (stupid me) for a fresh installation of Ubuntu 12.04 LTS, but before I looked with gparted because I did not want to lose my Vista partition.
Vista is on sda2, 88.4, flagged as boot. I tell to myself, fingers off from sda 2 and I will be just fine.

sda1   ntfs  PQserv  9.7 GB   diag
sda2 ntfs ACER       88.4 boot
sda3 extended        84.8 GB
sda5 ext 3             27.9GB *here I installed the 12.04 version*
sda6  Linux swap      1.8GB
sda7     ext 3          55GB
sda4  ntfs               3.2 GB

I install Ubuntu 12.04 LTS from USB in sda 5 (where Ubuntu 8.04 was). Reboot.
No OSs, error:

stage 1.5 grub error 2

From the official forums it looks like the best thing to do is to try linux secure remix with boot repair. 
I do it, live from USB (no install). Boot repair does not find any error in sda2.
[http://paste.ubuntu.com/5962122](http://paste.ubuntu.com/5962122)

In the text file boot repair recommends the following:

Recommended-Repair
This setting would reinstall the grub2 of sda5 into the MBR of sda.
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: 

unhide-bootmenu-10s   fix-windows-boot

=================== Settings chosen by the user
Boot-Info
This setting will not act on the MBR.



I do boot repair, "Boot repair successful". Grub now works but no OS is there.
In the grub menu now I have:


linux 3.5.0-23 generic -- starts with low resolution -->       Error: standby one minute while the display restarts - crashes and switches off    
linux 3.5.0-23 generic recovery environment: lands on Recovery menu (resume-clean-dpkg-failsafex etc) from where I don't quite know where to go.
mem test
mem test
Windows recovery environment on sda1 Windows: fail: cannot find file on C:D2D\images\*.WSI (I actually did not expect to boot from sda1, never did it before)
Microsoft windows XP embedded on sda4: fail:  insert disk (which of course I don't have, I never booted from sda4 before BTW)

No sda2. Now I run bootrepair analysis a second time.

[http://paste.ubuntu.com/5962193](http://paste.ubuntu.com/5962193)





In the file it says:  sda2: 

__________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista: NTFS
    Boot sector info:  No errors 

found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

As a recommended repair it suggests:

Recommended-Repair. This setting would reinstall the grub2 of sda5 into the MBRs of all disks (except USB without OS).
Grub-efi would not be selected by default because: no-win-efi
Additional repair would be performed: unhide-bootmenu-10s   
fix-windows-boot

This time I decided NOT to perform the recommended repair and ask you guys before.


Sorry, but my priority is not to lose the Vista partition, I have unfortunately to use it for work with some MS-only software. :) 

Can I force grub boot from sda2? With removal of the Linux OS will I make the situation even worse?

I enclose a screenshot from gparted now and a backup I made with the live linux secure remix.
Hope somebody can have some brilliant :idea::idea: thanks a lot for your help (badly needed  :) ) 
 

PS I am not even sure if I have to send the [http://paste.ubuntu.com/5962122](http://paste.ubuntu.com/5962122) to [email]boot.repair@gmail.com[/email] or if they will land on your desk anyway (I would like to avoid spamming) :)
Thanks again!

marco

---

### Post by oldfred on 2013-08-08
It looks like you installed grub to the PBR - partition boot sector of sda5. But now you do have grub installed to the MBR of sda which is correct.
The first error message about grub stage 1.5 would be from grub legacy. So you did not install grub2 into MBR but to PBR and old grub legacy could not boot.

But now you seem to have a partition issue. And system do not like partition issues.

      >  sda2: ___________________________________

       File system:       ntfs
    Boot sector type:  Windows Vista: [COLOR=#ff0000]NTFS[/COLOR]

  ```
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

   /dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,467,712   205,862,911   185,395,200   6 [COLOR=#ff0000]FAT16[/COLOR]

```    

System sees sda2 correctly as NTFS, but partition table now says FAT16. But you do not reformat a that would erase data.
From live installer you used to install.
You should be able just to use disk tools or disks (newer Ubuntu) and change partition type to 07 (NTFS). You can also use command line.

---

### Post by nyarlatotheph on 2013-08-09
> **oldfred said:**
> It looks like you installed grub to the PBR - partition boot sector of sda5. But now you do have grub installed to the MBR of sda which is correct.
The first error message about grub stage 1.5 would be from grub legacy. So you did not install grub2 into MBR but to PBR and old grub legacy could not boot.

But now you seem to have a partition issue. And system do not like partition issues.

        ```
 Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

   /dev/sda1                  63    20,466,809    20,466,747  12 Compaq diagnostics
/dev/sda2    *     20,467,712   205,862,911   185,395,200   6 [COLOR=#ff0000]FAT16[/COLOR]

```    

System sees sda2 correctly as NTFS, but partition table now says FAT16. But you do not reformat a that would erase data.
From live installer you used to install.
You should be able just to use disk tools or disks (newer Ubuntu) and change partition type to 07 (NTFS). You can also use command line.

Thanks a lot for the quick answer oldfred :)

Well spotted the change of format of partition! I am pretty sure I never touched the sda2, so no idea when it happened.
I cannot explain this discrepancy between system and partition table.
I kept on searching this night before following your suggestion and I found here the answer to the problem.

[http://www.linuxquestions.org/questions/ubuntu-63/grub-lost-my-windows-partition-can%27t-find-menu-lst-in-boot-grub-someone-can-help-841685/](http://www.linuxquestions.org/questions/ubuntu-63/grub-lost-my-windows-partition-can%27t-find-menu-lst-in-boot-grub-someone-can-help-841685/)

Apparently Grub2 sometimes "looses/misses" an OS at install time. 

```
sudo update-grub
``` did the trick.

Not sure what happened but now I can access Vista again.

Thanks!

Marco

---

