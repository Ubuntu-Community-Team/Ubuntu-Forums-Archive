---
title: "[ubuntu] Triple boot"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by hittingray on 2010-10-31
I want triple boot Windows 7, Ubuntu 10.04 and Fedora 13. I already have Windows and Ubuntu installed. I just wanted to know how to do this without screwing up GRUB (or the MBR for that matter). Do I just cancel Fedora installing the bootloader or will it pick up my dual boot like it says in the manual? 

If I cancel it, how do I add Fedora to the bootloader afterwards? I'm guessing:

```
sudo update-grub
```

Sorry if I ask some nooby questions, I've just never tried triple-booting before and this is my main, important computer (which also happens to be my only computer) and just want to be cautious.

Thanks

---

### Post by vader95 on 2010-10-31
Welcome to the Forum!!!

What grub does fedora use? 2 or legacy.

vader95

---

### Post by mick222 on 2010-10-31
Fedora uses Grub legacy I think it should detect you ubuntu and windows 7 installs

---

### Post by vader95 on 2010-10-31
I have successfully installed both ubuntu and openSUSE(which uses legacy) to the same hard drive as windows.  SUSE did not pick up ubuntu, but i got it working, so if you need help let me know.

---

### Post by georgemc on 2010-10-31
This is what I did to make a triple boot system with U10.04, Fedora 13, and Win2000.
 

 Before starting make sure you have any and all data backed up,  any recovery disks handy, your “live” CD/DVDs, and get yourself a copy of the “Super Grub2” disk (see reference below) just in case.
 
 Make sure you have some unallocated space.
 
 During this entire process proceed slowly and verify ever choice and click more than once to ensure you are targeting the correct partition.
 
 Since you already have a dual-booting system with Win7, the F13 system should just be a simple add-on.
 
 So I started with this and your setup should be similar:
 
 sda1 = w2000 (came with the Lap Top)
 sda5 = U10.04LTS with Grub2
 sda6 = swap
 sda7 = Home (Ubuntu's home dirs)
 unallocated space
 
 Natively F13 installs with a boot partition and a LVM setup for the rest.  This I did NOT get to work and “grub-update” did not find these partitions.  What I did make work was loading F13 on a normal partition and loading the F13 boot loader to that partition, not sure if the F13 boot loader is require but load it anyway.
 
 I didn't take any screen shots so you will just have to look at the F13 install options to set that up.  I used custom partitions and made sure that the boot loader will install on the F13 partition in my case that would be sda8, you most likely will have a different partition setup.  No need for multiple swap partitions, just use the Ubuntu swap partition, it should be of appropriate size already.   If you are giving F13 a separate home partition do not reuse Ubuntu's home partition, keep them unique.  
 
 After F13 and the F13 boot loader were installed I booted up into Ubuntu 10.04 LTS and ran “sudo grub-update” and made sure it found the OS's or partitions for a)  w2000, b) U10.04LTS, and c) F13.  I ended up with this configuration:
 
 sda1 = w2000
 sda5 = U10.04LTS
 sda6 = swap
 sda7 = Home (Ubuntu's home dirs)
 sda8 = F13 with F13 boot loader
 sda9 = Home (Fedora's home dirs)

 I DO NOT use the same “home” partition for U10.04 and F13.  Each has its own distinct “home” partition and directories.
 
 Boot up into F13 and get all the updates, most likely there will be a kernel update in there, then boot back into Ubuntu and run the grub-update, that should catch any F13 kernel updates.
 
 Notes:
 Partition names need to be unique.
 Since I am using the  U10.04LTS grub2 to maintain the boot menu, I have to use the U10.04LTS grub2 to update the boot menu after any F13 kernel updates.  Not a big deal just need to keep that in mind.
 And “swap is swap”, since this is dual/triple booting no need for multiple swap partitions.  So I just made sure that F13 found my sda6 swap partition and used it.
 Both implementations  U10.04LTS and F13 use the Gnome desktop manager.
 


 A big Thank You goes out to all the people who posted on this and the Fedora website.
 
Hope this helps.

 George

 Reference and Credits:
 
 Ubuntu post subject: How to Dual boot Ubuntu 10.04 and Fedora 13?
 [http://ubuntuforums.org/showthread.php?t=1529004](http://ubuntuforums.org/showthread.php?t=1529004)
 Ubuntu post subject: GRUB 2  A Guide for Users  
 [http://kubuntuforums.net/forums/index.php?topic=3106368.0](http://kubuntuforums.net/forums/index.php?topic=3106368.0)
 Fedora post subject: HowTo Install Fedora 10/11/12 DVD from a 4GB USB stick
 [http://forums.fedoraforum.org/showthread.php?t=205596](http://forums.fedoraforum.org/showthread.php?t=205596)
 Super Grub2
 [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by hittingray on 2010-11-01
Ok, so here's my setup: 

sda1: Windows 7
sda2: IBM Recovery (came with the computer)
sdb1: Storage (files, games etc.)
sdb2: iTunes (separate HDD for all my library)
sdb3: Swap
sdb4: Ubuntu 10.04 (Home is here as well, mounted at /)

And then 13GB of unallocated space which would become sdb5

Edit: I just remembered you can't have more than 4 primary partitions, so I'm going to backup and remove the Recovery and put the swap there and give Fedora the extra 2.3GB that the swap has on sdb.

2nd Edit: Should I mount Fedora at / as well? I have Ubuntu mounted there, will it make a didfference? (Sorry, noob at triple booting and dual booting 2 Linux systems >.<)

3rd Edit: Boot Info Script results file attached.

---

### Post by garvinrick4 on 2010-11-01
Any which way you want to partition your drives is up to you. All you have to do when
you install fedora 13 is to not install grub at all. There is a point in the installation of fedora
(anaconda I think the name is, the installation) where it asks you where to put grub just uncheck the box I believe and choose none. You get the drift just do not install a grub.
Then boot into Ubuntu install when done with Fedora install and:
```
sudo update-grub
```os-prober will go out and find your installs and put them in grub-config and your
boot menu and you will be set.
If you install grub legacy you will then have to run set of commands with live cd to get grub2 back in mbr (master boot record) as the grub device to use. Grub2 and grub legacy
do not like each other much so could turn into pain in the rear. Advise just to not install grub-legacy at all.

---

### Post by hittingray on 2010-11-01
That was the main answer I was looking for, thanks. I'm gonna go ahead with the installation now, I'll let you guys know how it goes and if anything goes wrong, thanks.

---

### Post by garvinrick4 on 2010-11-01
Here is a link for Fedora post installation guide. It is a bit different and not as user friendly as Ubuntu. But this guide will help some
fedora 12 and 13 post installation about the same.

[http://www.my-guides.net/en/content/view/174/26/](http://www.my-guides.net/en/content/view/174/26/)

---

### Post by hittingray on 2010-11-01
It seems to be stuck at package 1110 :/, dang.

After a couple of retries, I've finished installing it and no issues what so ever. Thanks

Edit: Cancel that, it has too many issues, including not picking up my GeForce 6200 and only my integrated one.

**How do I remove it without screwing up GRUB2 =.=" ** Can I just remove the Fedora partition and then "sudo update-grub" and that's all?

---

### Post by garvinrick4 on 2010-11-01
> **hittingray said:**
> It seems to be stuck at package 1110 :/, dang.

After a couple of retries, I've finished installing it and no issues what so ever. Thanks

Edit: Cancel that, it has too many issues, including not picking up my GeForce 6200 and only my integrated one.

**How do I remove it without screwing up GRUB2 =.=" ** Can I just remove the Fedora partition and then "sudo update-grub" and that's all? Yes just go into gparted and reformat to ntfs or ext4 or fat32. Delete will make it unallocatted space for future use if that is what you desire. NTFS or FAT32 will make it readable and writeable in linux or Windows. EXT4 will be just a linux partition. I do not see why the install went bad. Is it just graphic driver problems. I would try to reinstall again from scratch and download a new iso and burn new disk at slowest speed possible. Never had a problem installing myself. But yes you were right after removing just go into Ubuntu and sudo update-grub. All Linux OS's are a bit different if have proprietary drivers. I am sure your googled to see what the driver install is in Fedora for geforce 6200.

---

### Post by hittingray on 2010-11-01
Thanks so much for your help, just one last thing: I want to merge my Ubuntu partition and the free space I got from Fedora but GParted is giving me: [http://twitpic.com/332snr](http://twitpic.com/332snr)

Should I continue moving it? And if it doesn't work can you give me the commands to restore GRUB?

And the install went bad because I had to use my integrated to install it and it did not even pick up the other graphics card, even after installing the drivers =.=" I'm not going into the BIOS, changing from GPU to GPU, just to boot into another OS.

---

### Post by garvinrick4 on 2010-11-01
Give me a screen shot of the whole gparted screen and tell me what you want to move and where. Putting grub2 back in place is no problem but let me see what you are doing first.

---

### Post by hittingray on 2010-11-01
Just trying to merge the free space that was from Fedora (which was sdb3) with the Ubuntu partition (sdb4)

---

### Post by garvinrick4 on 2010-11-01
Would be more comfortable with seeing screenshot of gparted screen so I do not give you some funky advice. Moving left is more time consuming and takes a few procedures. Need screenshot to advise though. Take screenshot then hit paperclip up on Message box and upload from whereever you put file and will come out in Post when you hit submit reply.

---

### Post by hittingray on 2010-11-01
Ok, here ya go: [Click]("http://i128.photobucket.com/albums/p196/hitting_ray/gparted.png")

I'm on Ubuntu right now, so I can't merge the partitions while they're still mounted. (I'll switch to GParted's live CD after and if you're wondering, I'm using KDE right now, just installed it)

Basically, like in the picture, using the free space, resize sdb4 and make it larger

---

### Post by garvinrick4 on 2010-11-01
Use a live cd and open gparted:
Ok right click the unallocated space and format to ext4 hit green apply check on top of page.
Right click on Ubuntu partition and resize and move all the way over to fill unallocated
hit apply arrow.
Will take a while because moving has to move the complete install over.

If for any reason cannot resize Ubuntu after making unallocated ext4. Then delete the old fedora and make it back to 
unallocated then move over ubuntu to fill space.
The reason it might screw with grub is it most likely will give it sdb3 instead of sdb4 for Ubuntu install now and grub is looking
in sda4 for grub install. Can fix with a few commands let me know how it go's.

---

### Post by hittingray on 2010-11-01
So I should be fine and not have to fix anything?

---

### Post by garvinrick4 on 2010-11-01
> **hittingray said:**
> So I should be fine and not have to fix anything?
If the sdb number changes from sdb4 to sdb3 yes we have to reinstall grub about 4 commands or so. Right now you go from sdb2 to sdb4 so will in all rights change it to sda3.

---

### Post by garvinrick4 on 2010-11-02
You know you can just make it a data partition in just format to ntfs and use it in both Windoz and ubuntu for data.

---

### Post by hittingray on 2010-11-02
I already have one ;) I have a some large apps with huge libraries for files and I only had 2GB left, and everything turned out fine. Thanks for your help

---

### Post by garvinrick4 on 2010-11-02
> **hittingray said:**
> I already have one ;) I have a some large apps with huge libraries for files and I only had 2GB left, and everything turned out fine. Thanks for your helpYou are welcome enjoy your Ubuntu.

---

