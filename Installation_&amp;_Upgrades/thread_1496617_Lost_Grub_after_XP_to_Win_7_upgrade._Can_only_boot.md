---
title: "Lost Grub after XP to Win 7 upgrade. Can only boot into Win 7 now"
date: 2010-05-29
forum: Installation &amp; Upgrades
---

### Post by silvervein on 2010-05-29
I'm looking for some direct help. I keep finding the same fixes on the web and they are not working.
 
What I have/what I did:
 
I have a dual boot PC. HD0 was XP. HD1 Kubuntu 10.04. I upgraded XP to Win 7. This jacked my Grub up, now all I can load is Win 7. I don't see the Grub menu anymore.
 
I've been trying to reinstall Grub using varroius web pages like:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
-or-
[http://ubuntuforums.org/showthread.php?t=260625](http://ubuntuforums.org/showthread.php?t=260625)
-or-
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)
- and finally-
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)
 
They seem to all be telling me the same thing but not working.
 
I boot into a liveCD. I have to **sudo apt-get install grub**
then I can do **sudo grub**
 
I follow the instructions: 
sudo grub
> **root (hd0,0)**
> **setup (hd0)**
I get *"Error 17: Cannot mount selected partition"*
Now if I'm understanding this right the reason for that is. HD0,0 is my first HD first partition (which is Win 7), and grub doesn't like windows. 
 
I tried swapping it out so it reads
sudo grub
> **root (hd1,0)**
> **setup (hd1)**
I then quit and reboot. Win 7 loads. I don't see Grub.
 
What am I doing wrong. Am I having issues because I am using 2 separate hard drives?
 
Any assistance/suggestions are appreciated! 
 
(Although dumping Windows completely is out of the question. WINE and I are not friends when it comes to playing video games).
 
Thanks!

---

### Post by darkod on 2010-05-29
Those commands are for reinstalling grub1. 10.04 comes with grub2 and you shouldn't run them.
Because you were using live mode and didn't mount the root partition, lets hope there is no real damage. The grub package you installed in live mode is gone after you reboot.

First of all, if 10.04 was a clean install, not upgrade, you definitely have grub2 and need to use 10.04 cd. Boot in live mode again, and post the results of:

sudo fdisk -l (small L)

Once we have them, it takes just two commands to reinstall grub2. Hopefully we will figure out what we need from fdisk results without running more complicated procedures.

---

### Post by silvervein on 2010-05-29
Greetings darkod.

My install of 10.04 was an upgrade. I forgot to mention that, sorry. From what I've read online. I think I'm still running Grub not grub2, but I could very well be wrong. I tried the command you posted **sudo fdisk -l** Here is the display.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
16 heads, 63 sectors/track, 1938021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc60bf120

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      609524   307200064+   7  HPFS/NTFS
/dev/sda2          609525     1938018   669560976    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008551d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      120145   965064681   83  Linux
/dev/sdb2          120146      121601    11695320    5  Extended
/dev/sdb5          120146      121601    11695288+  82  Linux swap / Solaris

Now where should I go from here?

More detail if it helps. My first HD is partitioned 250Gig for Windows the other part is for data storage. The 2nd HD is all for Linux and is partitioned according to a general linux install.

Thank you for your assistance!

---

### Post by darkod on 2010-05-29
Grub2 started shipping with 9.10. So, if you had a clean install of 9.10 and then upgraded to 10.04, you still have grub2.

But if you also upgraded from 9.04 to 9.10, then to 10.04, grub1 might have remained all this time.

So, if you had a clean install, you do have grub2 and in that case you can just reinstall it with 9.10 or 10.04 cd in live mode, with:

sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb

You will also need to go into BIOS and set the ubuntu disk to be first in hdd boot order.

If you have any doubts, don't do anything, run the boot info script as explained here and either look at the results yourself or post them if you have any questions:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by silvervein on 2010-05-29
Actually I did upgrade from 9.04 to 9.10 to 10.04. Will this be an issue with the commands you listed.

I'm not too worried about losing any data. Before I upgraded xp to win 7 I backed up my information. Worst case scenario. I have to reload everything. Which for me the biggest pain is just tweaking everything back the way I like it. But no worries it's all experience. Try new things, break stuff, fix it and learn from it. Then use the knowledge to help others who have broken stuff. :)

---

### Post by darkod on 2010-05-29
In that case, run the script as suggested. It will show all the details needed.

Those commands won't work for grub1 but restoring grub1 is also easy.

Reinstalling 10.04 from scratch is up to you. :)

---

### Post by silvervein on 2010-05-29
Ok I've run the script and I believe this is the I'm looking for but I'm not understanding what I'm suppose to do with it.

[I]============================ Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe
                       /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files/dirs:

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:

=========================== Drive/Partition Info: =============================[/I]

Also in a previous post of yours you said "You will also need to go into BIOS and set the ubuntu disk to be first in hdd boot order."

I understand I would need to do this because grub will be located on that HD. However I didn't have to do that when I first installed xp and ubuntu. Is this something different because I went to Win 7?

Also the live CD I'm using is for 10.04. Would it be better if I just installed Grub2? If so what steps do I need to take. 

Thanks again for your assistance!

---

### Post by darkod on 2010-05-29
This is why the script is helpful. You didn't lose grub1, you still have it on the ubuntu disk:

[I]=> Windows is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the  same drive
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

[/I]Maybe you had another grub1 on /dev/sda that you were booting, and that one got overwritten by windows, but this grub1 on /dev/sdb seems it should work fine.

So, without reinstalling anything, if you go into BIOS and switch to boot from the ubuntu disk, will it work out OK?

---

### Post by silvervein on 2010-05-29
Swapping the Drives in BIOS worked. But I'm confused as to why I had to do that. Was it something with the Windows upgrade?
 
Now I need to update grub to show Windows 7 instead of XP, then I should be good to go. 
 
Thank you for your assistance.

---

### Post by darkod on 2010-05-29
I think you had grub1 also on your windows disk. And you were booting from that disk without even realising that. Upgrading windows deleted that grub, and since BIOS was still set to boot from that disk, it was just booting windows directly because windows bootloader can't see linux.

To go back to your question about grub2. Whether you have grub1 or grub2 doesn't depend only on the version installed on the MBR of the disk. More importantly, it depends which packages and settings are installed inside your ubuntu.

That is why installing grub2 now is not just executing one single command. You have grub1 inside ubuntu.

However, if you are interested, and since ubuntu is booting fine now, there was a command to execute to upgrade grub1 to grub2. With one single command, from ubuntu. I just have to find it now. :)

---

### Post by silvervein on 2010-05-29
That makes sense. Since I'm upgrading parts of my computer why not upgrade from Grub1 to Grub2. 
 
This might even help me fix Grub so I can boot into Windows 7. Grub1 still shows XP, and doesn't even mention Win 7. I tried **sudo update-grub**. But that didn't seem to work.

---

### Post by darkod on 2010-05-29
According to this:
[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

you should be able first to add the grub2 package with:

sudo apt-get install grub-pc

That will only create grub2 entry in your boot menu at first, so you can test if your grub2 is working fine after selecting it.

When you are satisfied it's working fine, you finish the upgrade process with:

sudo upgrade-from-grub-legacy

IMPORTANT: When it asks on which disk to be installed, you select the disk with Space and the * mark will appear. Just pressing Enter will close that windows with NO disk selected and grub2 not correctly installed.

Read that link, it has all the information.

---

### Post by darkod on 2010-05-29
> **silvervein said:**
> That makes sense. Since I'm upgrading parts of my computer why not upgrade from Grub1 to Grub2. 
 
This might even help me fix Grub so I can boot into Windows 7. Grub1 still shows XP, and doesn't even mention Win 7. I tried **sudo update-grub**. But that didn't seem to work.

Nope, that is for grub2 which automatically detects OSs.

For grub1, you need to edit the menu.lst with:

sudo gedit /boot/grub/menu.lst

At the bottom, find the windows entry and change the line starting with 'title' from Windows XP in Windows 7, or what ever you like. Save and close that file.

For grub1 you have to do manually like that. :)

---

### Post by silvervein on 2010-05-29
I tested out GRUB2. I'm defiantly going to upgrade to it. I'm at the stage where it asks where to load it. Here are my choices:

[ ] /dev/sda (1000204 MB, WDC_WD10EADS-00L5B1) 
[ ] - /dev/sda1 (314572 MB)  
[ ] - /dev/sda2 (685630 MB)  

[ ] /dev/sdb (1000204 MB, WDC_WD10EADS00L5B1) 
[ ] - /dev/sdb1 (988226 MB)  
[ ] - /dev/sdb2 (0 MB)   
[ ] - /dev/sdb5 (11975 MB)

Where do you recommend I load it. What is the most logical place and why?

Thanks! :)

---

### Post by darkod on 2010-05-29
Your ubuntu disk, /dev/sdb.

Mark using the Space bar just /dev/sdb, the MBR of the disk. Not any of the partitions on it.

Basically this is how you are booting now, using grub1 from /dev/sdb. This should just replace it.

---

### Post by silvervein on 2010-05-29
Yay!!! It all works! 

Thanks for your assistance darkod!!

Marking this as solved!

---

### Post by Mark Phelps on 2010-05-31
> **silvervein said:**
>  ... Now I need to update grub to show Windows 7 instead of XP, then I should be good to go...

GRUB2 generates boot stanzas based on the boot loader files it finds.  It generated one for XP because if found NTLDR.

If you're not using WinXPO anymore, you should be able to get that removed from GRUB by doing the following:
1) Remove the NTLDR file
2) Boot into Ubuntu and run "sudo update-grub"
3) Reboot Ubuntu. Should now no longer have an XP option.

---

