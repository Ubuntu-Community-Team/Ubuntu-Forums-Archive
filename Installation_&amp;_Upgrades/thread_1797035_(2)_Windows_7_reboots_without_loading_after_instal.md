---
title: "(2) Windows 7 reboots without loading after installing Ubuntu 10.04"
date: 2011-07-04
forum: Installation &amp; Upgrades
---

### Post by ashoktn on 2011-07-04
Hi,
 I freshly installed windows 7 (after leaving a partition for linux). Then i installed Ubuntu 10.04 from a usb. Now when i reboot, Grub shows windows 7 in the boot list, but it fails to load the os (automatically restarts after showing the windows logo).  I am facing same problem as posted in,  [http://ubuntuforums.org/showthread.php?t=1587103](http://ubuntuforums.org/showthread.php?t=1587103), but he had to reinstall everything again. Please let me know if there is any easier way out as everything seems to be fine when i run the  Boot Info Script (attached RESULTS.txt)
Thanks
ashok

---

### Post by oldfred on 2011-07-04
Welcome to the forums.

You seem to have normal windows files. You just have sda as the boot partition and sda1 as the main install, but that does not matter. Boot flag is on sda2. But grub does not use boot flag.

You may have to run repairs on windows. Do you have a windows CD that you can use for repairs? The repair finds the partition with the boot flag and tries to fix it.

If windows starts to boot, you may be able to hit whatever key it is to get into the repair/recovery enviroment. But when dual booting it is difficult as you have to hit key between grub and windows starting to load. Some say it takes many tries.

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub
chkdsk C: /r /f (may have to run /r or /f as separate entries) rerun until no errors
BootRec.exe /FixBoot  #updates PBR partition boot sector
BootRec.exe /ScanOs
BootRec.exe /RebuildBcd

---

### Post by ashoktn on 2011-07-04
Thankyou oldfred,
I tried the repair steps from a windows boot cd.
Now Windows 7 boots directly, but i am not able to load Ubuntu
(as you had warned!). 
The BootRec.exe /ScanOs step gave a message
###
Windows installations detected:0
###

Now please tell me how to boot to Linux?

I tried using easyBCD,
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

But i don't have admin rights on my windows account (School PC). Please let me know if i can add Linux to the boot list any other way
Thanks
Ashok

---

### Post by oldfred on 2011-07-05
You can reinstall grub2's boot loader which then should let you boot either. Are you supposed to be modifying system, if it is a school computer?

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

You can put a full install on an external hard drive or larger (8GB or more) flash drive and boot it if you can access BIOS to choose what to boot.

---

### Post by ashoktn on 2011-07-05
Thanks for the reply oldfred, 
I tried reinstalling grub from the liveCD (it has grub v1.98) and then did  update-grub.
Although update-grub detects windows 7 and adds it to the boot list, it repeatedly reboots just like before.

(now i got admin rights and some help, as this pc is assigned for my project)
We recovered the windows MBR and then installed  easyBCD to add a linux  .
Next installed grub on /dev/sda5 instead of /dev/sda . 

Now it works , although little annoying to go through both the boot loaders 
thanks again and pls let me know how to mark the thread as solved?

---

### Post by oldfred on 2011-07-05
Some here that use win7 a lot like EasyBCD, I do not use it (only have XP) and do not know much about it. I happen to like grub2.:)

See my signature on solved.

With grub2's boot loader installed to a partition you may have to regularly update it. It is less reliable as it uses blocklists which are hard coded addresses to find the rest of grub in the partition. If those files move on an update then it will not work until grub is reinstalled to the partition. Keep a liveCD handy and know how to reinstall grub2's boot loader.

---

### Post by ashoktn on 2011-07-05
i am still wondering why does grub2 does not load windows 7 properly. It does detect a windows installation on /sda2 (during update-grub)and i know that the windows is working fine when the windows loader is used.

thanks
ashok

---

### Post by oldfred on 2011-07-05
After you fixed windows boot, does the grub entry work? Or maybe something with EasyBCD now makes it that you cannot boot the entry from a partition and get back to windows.

Grub just jumps to the window partition to continue booting, just like the windows boot loader in the MBR jumps to the partition. Once there all the issues are windows issues.

---

### Post by Mark Phelps on 2011-07-05
Like other utilities, EasyBCD has an option that repairs/rewrites the Win7 Boot loader info (BCD).

However, also like the other utilities, it makes some presumptions when doing that and will often leave you with the simplest BCD possible.

I have a PC using EasyBCD and when I last did the repair, it recreated the BCD with only one entry.  I was able to add the other two entries manually, but it took some trial and error to get them working.

---

### Post by YesWeCan on 2011-07-05
> **ashoktn said:**
> Now it works , although little annoying to go through both the boot loaders 
If you edit [COLOR=Navy]/etc/default/grub[/COLOR] and set the line [COLOR=Navy]GRUB_TIMEOUT=0[/COLOR] you should not see the Grub menu.

---

### Post by ashoktn on 2011-07-05
thankyou guys,

Now i realized that i need a 64 bit version , so i had to reinstall .This time i used wubi to install ubuntu 10.04 64bit version. It worked flawlessly (still it uses the windows loader ) 

@ oldfred
When the windows boot was fixed in my previous installation i, the grub entry (for windows) doesn't work
But using the Wubi, the windows entry in the grub's list take me back to the windows loader .

---

