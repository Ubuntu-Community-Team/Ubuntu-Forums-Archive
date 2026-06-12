---
title: "Dual Booting XP in 10.04"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by RyanBate on 2010-04-19
I recently updated to the beta release of 10.04. The upgrade went smoothly in most regards. However, ever since upgrading, I can no longer boot into windows XP. The GRUB menu loads fine, and Windows is an available selection. When I choose it though, the screen goes black and I can't do anything. From within ubuntu I can see all the windows files. does anyone have an idea about what I might have done wrong and what I can do to fix this.

---

### Post by roynoblin on 2010-04-19
drs305 sent me this and it worked for me

[How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)]("http://ubuntuforums.org/showthread.php?t=1014708")

good luck

---

### Post by wilee-nilee on 2010-04-19
> **RyanBate said:**
> I recently updated to the beta release of 10.04. The upgrade went smoothly in most regards. However, ever since upgrading, I can no longer boot into windows XP. The GRUB menu loads fine, and Windows is an available selection. When I choose it though, the screen goes black and I can't do anything. From within ubuntu I can see all the windows files. does anyone have an idea about what I might have done wrong and what I can do to fix this.

If you have a true dual boot not wubi post this bootscript.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by RyanBate on 2010-04-19
Thanks for the quick replies! I have to wait till tomorrow to test them out, but the help is really appricated.
with regaards to what wilee-nilee said, how do i know the difference between a true dual boot and wubi? sorry if this is stupid question, still learning my way around this

---

### Post by kansasnoob on 2010-04-19
> **RyanBate said:**
> Thanks for the quick replies! I have to wait till tomorrow to test them out, but the help is really appricated.
with regaards to what wilee-nilee said, how do i know the difference between a true dual boot and wubi? sorry if this is stupid question, still learning my way around this

You can run the Boot Info Script with either, or from a Live CD:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

It provides most of the info one normally needs to troubleshoot boot problems.

---

### Post by wilee-nilee on 2010-04-19
> **RyanBate said:**
> Thanks for the quick replies! I have to wait till tomorrow to test them out, but the help is really appricated.
with regaards to what wilee-nilee said, how do i know the difference between a true dual boot and wubi? sorry if this is stupid question, still learning my way around this

A wubi install is installing Ubuntu inside of windows. I guess true dualboot is a misnomer, what is important though is are the operating systems side by side or is Ubuntu installed inside of Windows, but as kansasnoob suggests the boot script will tell us. I would be careful at trying the links information at this point in that you seem to not know the type of install it is. Back it all up if you can before doing anything, or at least back up what you want to save.

---

### Post by RyanBate on 2010-04-19
> **wilee-nilee said:**
> A wubi install is installing Ubuntu inside of windows. I guess true dualboot is a misnomer, what is important though is are the operating systems side by side or is Ubuntu installed inside of Windows, but as kansasnoob suggests the boot script will tell us. I would be careful at trying the links information at this point in that you seem to not know the type of install it is. Back it all up if you can before doing anything, or at least back up what you want to save.

Oh ok, I understand what you mean know. I am definitely dual booting then, as they run independant of each other and on their own partitions. I'll try the suggestions tomorrow, and see what happens

---

### Post by roynoblin on 2010-04-19
I am just starting with linux but I have installed more than one OS in one PC. I have done this both on separate HDD's and on the same HDD, just different partitions. In windows this is controlled by your boot log. It appears to me in ubuntu it is called GRUB. Different but the results are the same. They allow you to control the use of more than one OS in one PC.
 

 You appear to have the same problem I just got fixed with the help of a lot of good people on this forum. ubuntu worked fine but xp would start then the screen would go black and it was as if i had pressed the restart button. 

I built this PC to try linux and have windows installed just cause I'm used to it and have windows software that I need at times and to lazy to go to a different PC.:) 

In that there was not much in the windows partition that would need to be reinstalled, I reinstalled XP. I prefer to set separate partitions for the various OS and a separate partition for data storage. Here are some of the commands that helped me see the problem. I was able to get everything up and running with zero loss of data. NOTE: if you have data in the same partition that XP is in, do a backup. You can get an external HDD up to 3T that will meet most all needs that you can just plug into a USB port.
 

 Copy and paste the below in terminal and it will let you see where what is. The info scripe is a big help to see the big picture.
 

 to get a list of your partitions
 sudo fdisk -l
 or  
 sudo blkid
 

 How to update update grub
 sudo update-grub
 

 How to run info script after you down load it
notice this is different than the directions at info scrip

sudo bash /home/ubuntu/Downloads/boot_info_script*.sh

info script downloads to a download folder and properities gave me the correct path.
after running the above, the results will be in the download folder.

by starting ubuntu with cd, reading this [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
and all the above is what got me back up and running

---

### Post by RyanBate on 2010-04-20
> **wilee-nilee said:**
> If you have a true dual boot not wubi post this bootscript.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

ok so i ran the boot info script and have my results. It did find Windows on one of my partitions, and i posted the results in this post. From what I read off the results, there wasn't an apparent problem.

---

### Post by RyanBate on 2010-04-20
> **RyanBate said:**
> ok so i ran the boot info script and have my results. It did find Windows on one of my partitions, and i posted the results in this post. From what I read off the results, there wasn't an apparent problem.
sorry for successive posts, but i guess i should add my question. With these results, how do i know what the problem is with booting into windows??

---

### Post by presence1960 on 2010-04-21
you installed GRUB 2 onto the boot sector of the windows partition. You also had wubi installed at one time. See here:

```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    [COLOR="Red"]Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 129831265 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs:   /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr[/COLOR]

```

I would try fixing the windows hard disk so the windows bootloader is on the MBR. You can do that from ubuntu. Boot into ubuntu and open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings.

Next from terminal run ```
sudo lilo -M /dev/sdb mbr
``` Reboot & make sure your 80GB sda disk is set to boot before the sdb disk. At the GRUB menu try windows. 

If this does not work you may have to use the windows XP install disk & choose recovery and at the prompt run fixboot & fixmbr. The instructions for this are [here]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to the instructions for XP). Please note if you use the XP install CD you must make sdb first hard disk to boot prior to running those commands because windows always writes it's bootloader to the first disk to boot. After running fixboot & fixmbr make sda boot first again so you get the GRUB menu.

---

### Post by oldfred on 2010-04-21
You are the eighth post that I have seen the grub boot loader installed in the windows PBR. 

Did you use the advanced button on the install and check all the boxes on where to install grub or did it do it on its own? I have only gotten one to admit he check the boxes but we need to know if it is an outright bug or just a user issue with the install menu. I have not found a bug report on this yet.

---

### Post by RyanBate on 2010-04-21
> **presence1960 said:**
> you installed GRUB 2 onto the boot sector of the windows partition. You also had wubi installed at one time. See here:

```
sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    [COLOR="Red"]Boot sector info:  Grub 2 is installed in the boot sector of sdb1 and 
                       looks at sector 129831265 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  Windows XP
    [COLOR="Red"]Boot files/dirs:   /ntldr /NTDETECT.COM /ubuntu/winboot/wubildr.mbr 
                       /ubuntu/winboot/wubildr[/COLOR]

```

I would try fixing the windows hard disk so the windows bootloader is on the MBR. You can do that from ubuntu. Boot into ubuntu and open a terminal and run ```
sudo apt-get install lilo
```Ignore the warnings.

Next from terminal run ```
sudo lilo -M /dev/sdb mbr
``` Reboot & make sure your 80GB sda disk is set to boot before the sdb disk. At the GRUB menu try windows. 

If this does not work you may have to use the windows XP install disk & choose recovery and at the prompt run fixboot & fixmbr. The instructions for this are [here]("http://ubuntuforums.org/showthread.php?t=1014708") (scroll down to the instructions for XP). Please note if you use the XP install CD you must make sdb first hard disk to boot prior to running those commands because windows always writes it's bootloader to the first disk to boot. After running fixboot & fixmbr make sda boot first again so you get the GRUB menu.

Thanks for the help, I'll try it out as soon as I get a chance. It sounds like that'll fix the problem, as the symptoms seem to be related to a problem with my windows bootloader.

---

### Post by RyanBate on 2010-04-21
> **oldfred said:**
> You are the eighth post that I have seen the grub boot loader installed in the windows PBR. 

Did you use the advanced button on the install and check all the boxes on where to install grub or did it do it on its own? I have only gotten one to admit he check the boxes but we need to know if it is an outright bug or just a user issue with the install menu. I have not found a bug report on this yet.

Yes, when I updated, it requested that reinstall GRUB. Since I couldn't remember which partition housed which OS, I followed the recommendation of the updater, to install it to all partitions. Although after it was finished, it said it could not install it to 2 of the sections. If the grub boot loader being in the windows section is the problem, will presence1960's suggestion fix the issue?

---

### Post by oldfred on 2010-04-21
Yes presence1960's suggestions will work just fine. When you installed grub you only need to install it to the MBR. Windows has some of its files to continue booting in the partition boot record or PBR and when you installed grub, that part of the windows boot loader was overwritten. fixboot will put it back.

---

### Post by presence1960 on 2010-04-21
Thanks oldfred for helping out. I haven't been able to spend much time in here lately. Sometimes I'll post a suggestion and not be back for a day or so.

---

### Post by RyanBate on 2010-04-22
> **oldfred said:**
> Yes presence1960's suggestions will work just fine. When you installed grub you only need to install it to the MBR. Windows has some of its files to continue booting in the partition boot record or PBR and when you installed grub, that part of the windows boot loader was overwritten. fixboot will put it back.

Ok so i tried presence1960's suggestion, but to no avail. Is it possible I over wrote something on the Windows partition? Thats the only thing that I can think of. I think I'll try doing a repair of the windows CD, if I can find it

---

### Post by oldfred on 2010-04-22
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

