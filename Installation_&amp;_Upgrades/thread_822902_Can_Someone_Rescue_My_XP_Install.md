---
title: "Can Someone Rescue My XP Install"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by goofeyfoot on 2008-06-08
Hi again:

I had a dual boot Ubuntu 7.something plus Win XP.

I tried to add a drive and then grub went crazy.  Like an idiot I used Super Grub Disk, not really knowing anything about what I was doing.  Some choices in Super Grub Disk looked appealing like "repair master boot disk" and stuff like that.  Like a kid in the candy store I had to try everything, not having a clue.

So you can guess the rest.

Now I can't get to Windows at all.  I get errors like no NTTLDR and the system just hangs.  Stuff like that happens.

Can someone help me get Windows running again?  I sure would appreciate it.

Thanks again.

Michael

---

### Post by Pumalite on 2008-06-08
If Super Grub cannot boot your XP try fixing the MBR.

---

### Post by Rocket2DMn on 2008-06-08
To fix the MBR, boot from your Windows XP disc and enter the recovery console.  Once there, run
```
fixmbr
```
If you are still using Ubuntu as well, you will need to reinstall GRUB.  That can be done with your Super GRUB Disk, or by looking here - [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Rallg on 2008-06-08
Many XP-era computers came with XP "pre-installed" along with a "recovery partition" that could restore XP to factory state. No CD was shipped with the system, so fixing MBR from the installation CD could not be done. Using the recovery partition might not work if the MBR is wrong, and in any case it's a bad idea to use it unless your computer is only a few days old and has no personal files.

If you do have the XP installation CD, use it to fix the MBR, as mentioned above. If no CD, there are several alternatives.

The message "NTLDR not found" (or equivalent) suggests that your current MBR is pointing to a partition where it expects to find the Windows bootloader, but the bootloader is not there. Perhaps the MBR is pointing to where Grub was, or still is, and the software is confused.

First, put the Ubuntu live CD in and boot it. From Terminal:

ls -l /dev/disk/by-uuid

That will give you a list of hard drive partitions, and their UUID numbers. Note that normally /dev/sda5 would be known to Grub as (hd0,4) and /dev/sdb5 would be (hd1,4) where the hd index is one less than the sd index.

Poke around the hard drive file system. Can you find XP? Can you find your previous installation of Ubuntu? (Be sure that you are not looking at the live CD's own files, instead look on the hard drive.)

If Ubuntu is still on your hard drive, have a look at its /boot/grub/menu.lst file. Again, be sure that you are looking on the hard drive, not at the CD's own files.

Where do the various menu.lst entries point? Does it show (hd1,4 when it should show (hd0,4), or (hd1,6) or any other such mis-direction? How about the UUID numbers? Are they correct?

If you can locate a problem this way, then try manually correcting the hard drive menu.lst:

gksudo gedit DEVICE/boot/grub/menu.lst

where "DEVICE" is the correct path on the hard drive, not on the CD.

I don't have two hard drives, but from other forum posts I've noticed that some users with 2 drives have a problem where hd0 and hd1 have been interchanged. Look around for more info, if that's your problem.

If none of the above helps, then you might have to re-install Ubuntu so that its Grub bootloader can find XP.

---

### Post by goofeyfoot on 2008-06-08
Okay well there are plenty of ideas there and I think I understand what to try and the order in which to do so.

So this week I'll give her a go.

Let me thank you all for your insights and I'll try to write back to confirm success.

Best regards.

Michael

---

### Post by adrian15 on 2008-06-10
> **goofeyfoot said:**
> 
Let me thank you all for your insights.

Best regards.

Michael

Hi Michael. I've managed at last to bring back SGD website to life.
Here there is your answer:

[http://www.supergrubdisk.org/forum/index.php?topic=88](http://www.supergrubdisk.org/forum/index.php?topic=88)

adrian15

---

### Post by mhousel on 2008-06-12
Hi,

I have a similar problem in that my Windoze XP no longer boots after a recent upgrade of Ubuntu 8.04.

I have no alternative but to use the system restore disk that came with my Toshiba laptop. (Believe me I've tried everything including 4 hours on the phone with Microsloth!)

I completely wipes the HD. 

I've added lots of applications, set up my email, browser shortcuts, etc. etc. and would like to be able to recover that sort of stuff when I re-install Ubuntu.

 Is there any way to back up any portion of my WUBI installed and upgraded 8.04 installation so that I can get back to the current state when I re-install 8.04?

---

### Post by adrian15 on 2008-06-13
> **mhousel said:**
> 
I've added lots of applications, set up my email, browser shortcuts, etc. etc. and would like to be able to recover that sort of stuff when I re-install Ubuntu.

 Is there any way to back up any portion of my WUBI installed and upgraded 8.04 installation so that I can get back to the current state when I re-install 8.04?

Do you mean applications, and email from Linux or from Windows?

Did you install Ubuntu with the WUBI method without not creating any partition?

Thank you.

adrian15

---

### Post by mhousel on 2008-06-13
> **adrian15 said:**
> Do you mean applications, and email from Linux or from Windows?

Did you install Ubuntu with the WUBI method without not creating any partition?

Thank you.

adrian15
thanks adrian,

From Linux. Yes, I installed 8.04 using the WUBI method without creating a separate partition.  I did that because I was concerned about the effect of re-partitioning the drive with my Windoze installation in place.

Is there an advantage of one over the other?

My Windows 'data' primarily consists of source code that's checked in to a repository so data loss is not a problem on the Windoze side.

The full day or so to re-install my tools and other applications is...also the time I've spent getting Linux set up and installing the endless updates that have come in since...

Perhaps when I finally take the plunge and restore Windoze on my laptop I can pre-partition the drive such that the system restore disk restores one partition and Linux can be installed on another?

Either way it will require that the HD be completely erased and re-formatted by the recovery disc that came with the system.

---

### Post by adrian15 on 2008-06-14
> **mhousel said:**
> thanks adrian,
From Linux.

Ok.
> **mhousel said:**
> 
 Yes, I installed 8.04 using the WUBI method without creating a separate partition.  I did that because I was concerned about the effect of re-partitioning the drive with my Windoze installation in place.

Is there an advantage of one over the other?

I prefer the manual partitioning because I know how it works and because WUBI is known to have some problems with ntfs mounts.

> **mhousel said:**
> 
My Windows 'data' primarily consists of source code that's checked in to a repository so data loss is not a problem on the Windoze side.

Ok.

> **mhousel said:**
> 
The full day or so to re-install my tools and other applications is...also the time I've spent getting Linux set up and installing the endless updates that have come in since...

Linux has user customisation. Ok.


> **mhousel said:**
> 
Perhaps when I finally take the plunge and restore Windoze on my laptop I can pre-partition the drive such that the system restore disk restores one partition and Linux can be installed on another?

It depends on the system restore disk depending on the system recovery partition or not!

> **mhousel said:**
> 
Either way it will require that the HD be completely erased and re-formatted by the recovery disc that came with the system.
Usually, it's what happens yes.


In theory you should be able to boot from a live cd and mount your ntfs partition and then loop mount the wubi image (I actually do not know which kind of image it is)... Once you have sucessfully mounted the wubi image you will be able to extract the /home/yourname contents, in other words, your user customisation.

I hope that someone else helps you. You might need to mount the ntfs with errors and I do not know what's the wubi img help.

Anyone else want to help mhousel?

adrian15

---

### Post by mhousel on 2008-06-21
I have re-partitioned my HD, moved Ubuntu to it's own partition and then everything seemed to be going OK.  I could still boot my damaged WinXP and Ubuntu just fine.

But, when I restored my Windoze installation it wiped the NTFS partition and now the option to boot Ubuntu is gone.

Asking about this in other threads I got something about making sure that wubildr is in C:\ so that the line in boot.ini can refer to it.

But since I can't boot Ubuntu or see the other partitions from WinXP I can't get that file.

Is there another source of this file short of a full WUBI re-install?

I also tried grub4dos where I placed grldr at c:\.

This allows me to get to the grub menu where Ubuntu now wants to boot from hda(0,0) rather than hda(0,2) the linux partition.

I can edit this (but it doesn't stick) and Ubuntu then tries to boot but ends up at initramfs: where I'm stuck.

I'm getting closer but still not there.

thanks

---

