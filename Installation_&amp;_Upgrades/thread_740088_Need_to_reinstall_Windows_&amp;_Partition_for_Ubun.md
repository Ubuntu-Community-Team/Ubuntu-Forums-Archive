---
title: "Need to reinstall Windows &amp; Partition for Ubuntu again."
date: 2008-03-30
forum: Installation &amp; Upgrades
---

### Post by sgbrix on 2008-03-30
My installation of Ubutu did not go well. I took a new drive and made a partition for Wk2 50g on a 200g drive.. Installed fine except that Ubuntu  installed over on the same partition and wiped windows completely of, my fault probably. 

So when I try to start from the beginning again and try to re-install Wk2 the Grub kicked in and stopped the Wk2 disk to start setup and to reformat the drive. Yes, Bootorder  been changed all different ways.

I made  several ways with bootdisks (a drive) to get stated but constantly run into that Ntldr is not found or a Grub 22 problem, can't be loaded, no ntdetect, fdisks, I'm  totally screwed up. Maybe I''m  not Ubuntu bound?

After a good night sleep I re-installed Ubuntu on the whole drive in the idea of then to shrink it and re-partition the drive after the fact as I told you can do. Well, installation came to an end and asked to re-boot, but now Ubuntu do not start at all from the drive, blank screen. Still can't reformat via a window disk and start again. Did another re-install, still the same, did all this playing around just kill the drive?

I hope I explained this right. This is  my first try into  linux, some ride it is. Does the work help mean anything?

---

### Post by Pumalite on 2008-03-30
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it
Delete everything in your hard drive. Click in this unallocated space and make 2 'New' partitions. The 1st, at the beginning of the drive (sda1) for Windows, formatted ntfs
The second, at the 'end' of the drive, for ubuntu, formatted ext3.
Then install Windows in the first partition and Ubuntu last to the 2nd partition. Go 'Manual' and delete this 2nd partition, make 2 'New' partitions:
Almost all (less 1gb) for '/'
The rest for /swap
Then press 'Forward'

---

### Post by forestpixie on 2008-03-30
Have you still got the livecd and does it boot ok? Assuming it does I would boot that, open a terminal - apps >accessories - copy this command and post the output please.

```
sudo fdisk -l
```

Edit - or do that instead :)

---

### Post by prshah on 2008-03-30
> **sgbrix said:**
> 
So when I try to start from the beginning again and try to re-install Wk2 the Grub kicked in and stopped the Wk2 disk to start setup and to reformat the drive. Yes, Bootorder  been changed all different ways.

I made  several ways with bootdisks (a drive) to get stated but constantly run into that Ntldr is not 


Boot off your Windows boot disk, and run ```
 fdisk /mbr
```; that will wipe the boot sector clean. While you are at it, run fdisk and delete any "non-dos" partitions. Note that if you want to delete a non-dos "logical drive" in an extended partition, you will have to use the linux live CD.

---

### Post by sgbrix on 2008-03-30
Thanks guys. I did a CD with Gparted, but the problem is the same, Grubs starts before CD even after boot order is set for CD. I finally got Ubuntu installed and is working right now. So problem remain. Will try Forestpixie's suggestion next.

---

### Post by Pumalite on 2008-03-30
You might need to DBan your drive before using Gparted: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)

---

### Post by sgbrix on 2008-03-30
Forestpixie, did the command and see Device, Boot Start, End etc,  and then what? Remember I'm completely new here.

Edit: Here's what the command line gave me:

> Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60484a5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24228   194611378+  83  Linux
/dev/sda2           24229       24321      747022+   5  Extended
/dev/sda5           24229       24321      746991   82  Linux swap / Solaris

---

### Post by forestpixie on 2008-03-30
What state are you actually in - what's installed and what's not and what do you need to do.

Run the command again and post the output here

and don't double post - [http://ubuntuforums.org/showthread.php?t=740113](http://ubuntuforums.org/showthread.php?t=740113)
apart from anything else noone quite knows what is going on.

---

### Post by sgbrix on 2008-03-30
Sorry for my double post, just getting desperate. Hoping to go back tonight with a working computer.

Buntu is now installed on the entire drive. Need to get win2k back on a partition of the drive, so I can finish my work for school. Like to have it set up for dual boot.

---

### Post by forestpixie on 2008-03-30
Boot with gparted and resize the buntu partition for the win install _ as much as you feel you need. Once you've resized the partition create a new ntfs in the space oyu've made and use it to install win2k on. 

At that point assuming you have installed win2k and it boots - ubuntu will no longer do so as win installs remove grub. You can fix it either with the livecd or using supergrub - this page details that 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Do you know you could run win2k from within ubuntu with a virtual machine.

---

### Post by sgbrix on 2008-03-30
Thanks for your input. 

Look at this point I would like to just know how to wipe the drive completely clean, no leftover Grub etc. Clean as in a new drive, so I can begin again and install windows and then Ubuntu I would be very happy.

---

### Post by Pumalite on 2008-03-30
The answer is in post # 6

---

### Post by sgbrix on 2008-03-30
I did that and get this:

"dban-1.07_i386.exe" cannot be opened
No application suitable for automatic installation is available for handling this file.

---

### Post by forestpixie on 2008-03-30
As you've got buntu working - get the .iso and burn it as an .iso and you'll boot with it

---

### Post by sgbrix on 2008-03-30
I accidentally booted from a CD with the .exe instead of the .iso the first time. That's what gave me the error. However, now when I boot off a CD with the dban-1.0.7_i386.iso file, it starts me up into Ubuntu normally, rather than to the boot prompt. I'm stumped. 

I'm unfamiliar with .iso files. So was there anything I was supposed to do rather than just burn the .iso to a CD??

---

### Post by Pumalite on 2008-03-30
Make sure you burn it as an 'image' and not as 'data'. Also make sure CD is first in the boot order in BIOS.

---

### Post by sgbrix on 2008-03-30
Ok so I burned an image file and now I get the right blue screen up [http://www.security.ku.edu/download/DBAN_Tutorial.pdf]("http://www.security.ku.edu/download/DBAN_Tutorial.pdf")
but after starting DBAN  and trying all the settings option in F4 it stops and hangs. I guess now we are into another area other than Linux and Ubuntu.

Is there any other way to get the drive wiped that you know of?

---

### Post by forestpixie on 2008-03-30
Boot with gparted - delete all partitions - apply and start again with creating your partitions - put the win one at the front

---

### Post by sgbrix on 2008-03-30
Booted up with disk and gparted-0.3.6

Open the main folder and run GParted after menu comes up to ask if I want to run in terminal, display, cancel, run, choosing run nothing happens. Same with the install folder. If I choose display I see first entry as [Desktop Entry] Encoding etc, but run it will not? plenty of files with data in all of them.

Is there any other way to go here?

---

### Post by Pumalite on 2008-03-30
Get version 0.3.4-0
It will be easier. At the boot prompt, just press 'Enter'

---

### Post by sgbrix on 2008-03-30
I downloaded gparted_0.3.3 to .6 and the result is the same. I am doing something totally wrong somehow, but I have to give up for now. Got to leave. Will try some other time to see how I can get the drive wiped clean. Thanks all.

---

### Post by sgbrix on 2008-04-06
A final note.

Never could reclaim the drive no matter what I did. But my solution arrived a few days ago, a new drive. Loaded my win2000 in that and dual boot with the original drive with Ubuntu, which by the way never did quit after all we tried to hit it with. 

If someone do have a step by step link for reclaiming a drive with Ubuntu please post her, so future souls can find the right answer.

Reclaiming a disk with win2000, just boot up to the installation CD and press enter.

SG Brix

---

