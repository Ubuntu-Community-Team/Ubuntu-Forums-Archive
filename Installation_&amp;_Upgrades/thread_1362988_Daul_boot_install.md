---
title: "Daul boot install"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by Reddoug on 2009-12-23
Hi
   Trying to install Ubuntu 9.10 on Vista 64 bit HP laptop. AMD 2.2 with 4GB of ram. Comp has a recovery partition. Found out the hard way that Ubuntu did differentiate between recovery and vista partitions and overwrote my Vista partition. No big deal. It showed both when I told Ubuntu not to overwrite complete HD. I reinstalled Vista and tried it again. This time I could see where I messed up but I do not know how to get around my problem. When I got to the partition screen, top line showed three partition but the line bellowed it only showed two partitions that it would create, recovery and Ubuntu. Is there away to do this and have three partitions? I am new to Ubuntu. 

Thanks, Doug

---

### Post by raymondh on 2009-12-23
> **Reddoug said:**
> Hi
   Trying to install Ubuntu 9.10 on Vista 64 bit HP laptop. AMD 2.2 with 4GB of ram. Comp has a recovery partition. Found out the hard way that Ubuntu did differentiate between recovery and vista partitions and overwrote my Vista partition. No big deal. It showed both when I told Ubuntu not to overwrite complete HD. I reinstalled Vista and tried it again. This time I could see where I messed up but I do not know how to get around my problem. When I got to the partition screen, top line showed three partition but the line bellowed it only showed two partitions that it would create, recovery and Ubuntu. Is there away to do this and have three partitions? I am new to Ubuntu. 

Thanks, Doug

Am a bit confused.

Kindly ...

1.  Boot into the Ubuntu liveCD and go live session (try ubuntu...)
2.  In live session, access gparted (system > admin > partition editor)
3.  When gparted window opens, press PRNTSCR (print screen) key which on my laptop is top right of the keyboard.  Save the visual to your desktop
4.  Come back to this thread and in your next post, click ATTACH (amongst the tools on top beside the smiley face) .... browse for the visual which was saved in desktop .... upload.
* If you don't have the prntscr key, you can use the camera (applications > accessories).

The gparted screenshot will help the forum visualize what your HD ocntains.

Also, you do have Vista working a well as the recovery partition, right?

Thanks.

---

### Post by Reddoug on 2009-12-23
Hi 

I have attached the screen shot. 

Thanks, Doug

---

### Post by raymondh on 2009-12-23
Thanks for the screenshot effort, Doug.

You want to install another Ubuntu making tis a 3-boot?  If yes, want to do a manual install, creating the partition beforehand and during the install process, installing unto it?  

Right now, I see Vista (sda1) which is Primary ..... Recovery (sda2), also Primary ..... Extended (sda3) housing logical partitions sda5,  a linux root, and sda6 swap.  You're allowed 1 more primary partition or, you can make as much logical partitions for as long as they (logical) are inside the extended (sda3).  That said, where do you want to get the space from ... sda1 or sda 5?

If you do not wish to install another ubuntu .... do you want to install OVER your existing linux root install, sda5, keeping this a dual-boot?  If so, that can also require a MANUAL install in step 4.

Sorry, am trying to re-read your first post VS. your screenshot and am still not clear.  I guess it's because I already see a linux install in your screenshot vs. your first sentence "Trying to install....".

Regards,

---

### Post by Reddoug on 2009-12-24
I do not have Ubuntu installed unless it is left over from my first try at installing it. I let windows reformat HD from when I reinstalled it from recovery partition. I have an fdisk and I will do a little digging. could it be Windows is not seeing the Ubuntu partition? Mt plan was to use some of the Vista partition. I do not need 280 GB of free space. The recovery partition is 13 GB. Thought I would give Ubuntu 75GB of space.

Thanks, Doug

---

### Post by raymondh on 2009-12-24
> **Reddoug said:**
> I do not have Ubuntu installed unless it is left over from my first try at installing it. I let windows reformat HD from when I reinstalled it from recovery partition. I have an fdisk and I will do a little digging. could it be Windows is not seeing the Ubuntu partition? Mt plan was to use some of the Vista partition. I do not need 280 GB of free space. The recovery partition is 13 GB. Thought I would give Ubuntu 75GB of space.

Thanks, Doug

When you re-installed windows from the recovery partition, it probably only reformatted sda1, which is a NTFS formatted partition....effectively leaving your 'first-try-ubuntu-install' intact since they are in ext format.

You could:

1.  Re-install GRUB2 which would see the Ubuntu install and then work on any problems/tweaks that particular install requires or;
2.  Re-install Ubuntu once more..... either thru
- manual install in step 4 where you would highlight the intended partition, select the proper mountpoint (/) and format.  For swap, you only need to select the existing swap partition and just mount or;
- delete sda5, sda6 and sda3 in that order thus leaving the space (75gb) unallocated then install ubuntu.  In step 4 of the installer, you can select "use largest continuous space" or;
3.  Boot into win7 and access the disk management utility.  Use that to:
- delete the ubuntu partitions (5,6,3)
- enlarge/extend sda1 to occupy the space
- Run defrag 2x to organize the HD
- Make sure win 7 boots ok
and then boot into the ubuntu liveCD and install.  This time, in step 4, selecting GUIDED RESIZE and using a slider to allocate OS' sizings.

So many choices.

Regards,

---

### Post by Reddoug on 2009-12-25
Hi 

   Thanks for the help. I removed partitions in Windows and then I told Ubuntu to use free space. Next step is getting the wireless network to work.

Thanks again, Doug

---

### Post by raymondh on 2009-12-25
> **Reddoug said:**
> Hi 

   Thanks for the help. I removed partitions in Windows and then I told Ubuntu to use free space. Next step is getting the wireless network to work.

Thanks again, Doug

You're welcome.

You can mark this thread closed/solved and create a new thread about the wifi 'challenge'.  In that thread, post your wifi card details as well.

Happy holidays.

---

