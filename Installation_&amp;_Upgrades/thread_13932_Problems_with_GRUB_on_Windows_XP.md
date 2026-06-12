---
title: "Problems with GRUB on Windows XP"
date: 2005-02-03
forum: Installation &amp; Upgrades
---

### Post by ramin on 2005-02-03
Hi all,

Recently, I tried to install Ubuntu on my home PC (Dell Pavillon, PIV). I have to HDs, hda has 30G and hdb 80G. Windows XP is installed on hda (just one partition). hdb has two partitions: 40G NTFS (1st partition) and 40G Free Space (2nd partition) as reported correctly by Ubuntu's install program. 

Now, everytime I install Ubuntu on hdb (2nd partion), everything goes well until it asks me to install GRUB because it has correctly detected my Windows XP. When the my PC gets rebooted (w/out any CD in the CDROM), I get an Error 21H !!!! Reminds me of the jurasic XT's!! Thank God I had my XP CD and was able to clean MBR thru the repair console (FYI, after login to the console run fixmbr and say 'y').

How do I remedy this problem. The first stage of the installation seems to be perfect, I  see: 

hdb1 NTFS
hdb2 ext3
hdb3 swap

BTW, I don't want to setup GRUB on diskette. You're help will make me a happy Ubuntu user.

  :D

---

### Post by Buffalo Soldier on 2005-02-04
According to the [GRUB manual](http://www.gnu.org/software/grub/manual/grub.html), error 21:> Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system.

Maybe the entry for your linux partition was set wrongly in GRUB. I assume your Ubuntu partition is at **hdb2** (which you already set it to ext3). Then the entry in /boot/grub/menu.lst should be something like:```
title		Ubuntu, kernel 2.6.8.1-4-386
root		**(hd1,1)**
kernel		/boot/vmlinuz-2.6.8.1-4-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.8.1-4-386
savedefault
boot

```

You can edit your GRUB entry during boot. Just highlight the *Ubuntu, kernel 2.6.8.1-4-386* during boot and then hit the **E** key if i'm not mistaken to edit your GRUB entry. Just follow the instruction at the bottom of your screen.

---

### Post by thestarman on 2005-02-04
ramin,

    It would have been more fruitful if we could have seen here what the actual settings in your GRUB menu.lst file were!  Tell you what, if you go to one of my site mirrors, here: [http://therdcom.com/asm/mbr/BootToolsRefs.htm](http://therdcom.com/asm/mbr/BootToolsRefs.htm) .  You can find tools for saving your MBR and even the whole first track (63 sectors) of the drive... that way you will never have to go all the way through the Ubuntu install all over again to reuse the GRUB MBR sector as it was written, nor just to edit the "menu.lst" file again!!!  We really need to see what is listed in this file: "**/boot/grub/menu.lst**" in order to give you specific help... and inclucing a listing of the output of the fdisk command:  **fdisk -l  /dev/hda**   (or /dev/hdb, etc.) would also be helpful.

The Starman.

---

### Post by ramin on 2005-02-04
Thanks guys for your help.  The problem is that I don't even get to see my Ububtu let alone Windows and GRUB menu. What  happens after the 1st phase of the installation, once I agree to install GRUB ,  is that the PC gets rebooted and I only see GRUB's version info, Grub's loading msg  abd the Error 21H. At this point my PC is dead cold!

Last night I tried to install the base system and the rest of the pkg's w/out installing GRUB. What I had in mind was to reboot w/ the CD and mount the secound drive manually and then do: 'grub-install /dev/hdb2'. Problem, the Shell from the install CD doesn't have fdisk cmd, I wanted to do 'fdisk -l' to see my detected drives.  Like it was mentioned above, somehow GRUB don't see my second drive, because just manually trying to mount to /dev/hdb2/3/4/5/... failed

Is there a way to install GRUB separately with my XP (1 OS for now), then I install Ubuntu? Do you think that would help? 

BTW, I have a DELL Dimension 4550 with two HDs ( 30G, 80G). 
Thanks a lot for your comments.

---

### Post by Buffalo Soldier on 2005-02-04
This is a long shot, but try pressing ESC while the pc reboots / when you see GRUB's version info. Maybe it will pop up some kind of menu.

---

### Post by brousch on 2005-02-04
Could this be a >1024 cylinder problem? I see that Ubuntu is installed on the back half of an 80 Gig HD ...

For more information, see this page:
[http://www.pcguide.com/ref/hdd/bios/sizeMB504-c.html](http://www.pcguide.com/ref/hdd/bios/sizeMB504-c.html)

---

### Post by Buffalo Soldier on 2005-02-04
I found this at LinuxForums.org, hope it can help you . [Solving Boot Problems with Grub](http://www.linuxforums.org/forum/topic-19999.html)

---

### Post by MySchizoBuddy on 2005-10-21
my harddrive is connected through a controller card. and fdisk -l says that my harddrive is /dev/hdi . but grub doesn't install. is there any special commands to use if ur harddrive is conneted through a controller card

---

