---
title: "GRUB GEOM error with 9.1"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by bpb_21 on 2010-01-06
I've been searching around and this is driving me crazy!  Ok, I've got an Acer Travelmate C100 (one of the first tablet PCs, I think) and I hooked up an external (USB) CD/DVD drive to install Ubuntu 9.10.  Much to my surprise and delight, everything works completely when installed - even the "tablet" aspect of the PC.

I just have one incredibly nagging problem: when I try to boot, I get the "GRUB GEOM error" message.  But, if I leave the CD/DVD attached, start the live CD and then select "boot from the first hard drive" it works fine.

I've searched on the forums and found threads where people are trying to dual boot with WinXP.  Ubuntu is running better than WinXP Tablet PC edition ever did, so the only OS on the PC is Ubuntu.  No dual boot or RAID or anything like that, and only one hard drive.

I also ended up on this site [http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error](http://en.opensuse.org/SDB:The_Boot_Process_Hangs_with_the_Message_GRUB_Geom_Error)
and as best as I can determine my problem has to do with #4 listed under "Cause:".  But, I've only got two partitions, one being the swap, and I don't know how I could get the boot loader any closer to the front of the hard drive since Ubuntu is the only OS on there.

Does anyone have any suggestions for this?  I'm so close to getting this working it's (again) driving me crazy!  Any help is greatly appreciated!

---

### Post by bpb_21 on 2010-01-07
I finally figured it out.  Apparently Ubuntu 9.10 kernel and grub2 use UUID numbers and some old BIOS-es don't recognize/support this.  So, I installed Lilo, using it as the main boot loader and basically reworked the /etc/fstab file to refer to the hard drive partitions as /dev/sda and so forth, instead of the UUID numbers.  Now it actually boots up on it's own (no Super Grub boot CD or otherwise needed) and it works better than it ever did with Windows XP Tablet PC edition!

So, install Ubuntu from the live CD, then boot to the newly installed Ubuntu on hard drive with the help of the live CD.  Then, follow the directions here [http://members.iinet.net.au/%7Eherman546/p4.html]("http://members.iinet.net.au/%7Eherman546/p4.html")

It's so easy even I can do it!  I just wish I'd found it about 36 hours ago...

---

### Post by krlloyd on 2010-01-17
I read your first entry and it could have been me.  I even discovered that boot from hard disk option on the live cd worked.  
Thanks so much for solving the problem.
In the lilo install instructions at the link you reference, there are several options: 

[            Install Lilo with apt-get]("http://members.iinet.net.au/%7Eherman546/p4.html#Install_Lilo_from_terminal") - from terminal in a running system                
           
[       Install Lilo with Synaptic Package Manager]("http://members.iinet.net.au/%7Eherman546/p4.html#Install_Lilo_from_Synaptic_Package_Manager")...(in a running system)

[Install Lilo from a Linux Live CD]("http://members.iinet.net.au/%7Eherman546/p4.html#Install_Lilo_from_a_Linux_LiveCD")...An emergency method for installing Lilo.
                                                          (Even works for an non-bootable Ubuntu installation)

[             Install Lilo from Breezy Install CD]("http://members.iinet.net.au/%7Eherman546/p4.html#Install_Lilo_from_Breezy_Install_CD")...An emergency method for installing Lilo.
                                                          (Even works for an non-bootable Ubuntu installation)

Which did you use?

---

### Post by bpb_21 on 2010-01-17
Well, they all end up on the same page so what I did was boot up from the "first hard drive" using the live CD to start.  Then I just ran Synaptic Packet Manager and found "lilo".  I installed that and then skipped to the part of that page where it talks about configuring lilo (or running liloconfig).

One note of caution: I tried installing Ubuntu with LVM and with encrypted home directory.  I couldn't apply the fix with either of these options.  I had to install Ubuntu with "Guided - use entire disk" and no encryption or LVM.  That's definitely due to my limited understanding of Linux, I'm sure, but be aware that you've got a reinstall on your hands if you select those options then try this method.  Good luck and post back if you have any problems!

---

### Post by krlloyd on 2010-01-17
Thanks for the quick reply.  
I did the install using synaptic package manager.
on the ubuntu 9.1 install I selected guided, use full disk on install.  

I seem to be stuck getting liloconfig to  like my edits of /etc/fstab 

I hashed out the UUID and replaced with 
#UUID=1a06c223-4cbe-4eb3-aae7-43dld848e913 ext4 errors-remount-ro 0 1
/dev/sda1 /media/sda1 ext4 errors-remount-ro 0 1

same for the swap entry
/dev/sda5 /media/sda5 swap sw 0 0 

the sda1 and sda5 came from the blkid command     $ sudo blkid 

liloconfig is saying /etc/fstab does not contain a valid entry for root file system

---

### Post by bpb_21 on 2010-01-17
Look at mine below.  I commented out the CDROM because I don't normally have that hooked up.  I noticed on the line where you have your swap file, the entry for "mount point", "none", wasn't there.  Also, note where I've got /dev/sda1 [tab] / [tab] ext4 and so on.  Don't forget to add the / in there to tell it that /dev/sda1 is the root.  Those lines with the UUID just wrap around.  I ended up commenting the entire file out and then retyping the needed lines.  I hope this helps some.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# / was on /dev/sda1 during installation

#UUID=b0d65bff-285c-4d1d-8aa0-287d8ddda2f3 /               ext4    errors=remount-ro 0       1

/dev/sda1	/	ext4	errors=remount-ro	0	1

# swap was on /dev/sda5 during installation

#UUID=6ab0a03b-d3a2-4208-ad85-37bfc93410f3 none            swap    sw              0       0

/dev/sda5	none	swap	sw	0	0

#/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by krlloyd on 2010-01-17
That was exactly it ( your note about having only a / in my sda1 line )
  Had i copied the instructions more accurately i would have noticed that.

This C100 is booting correctly now... not a super speedy machine:)
   
( I actually rescued this from a recycle bin - the battery only lasts a short while, and there is no wifi card or antenna in this one, those are left as an exercise ) 


Thanks so much!!:KS

---

### Post by bpb_21 on 2010-01-17
Glad it helped.  On mine it actually gets to running pretty good (for basic tasks, that is - like writing this post).  It is maxed out with 256MB RAM.  Plus, I can get about a good hour out of the battery.  In the BIOS there's a setting where you can chose between either using the integrated wireless card or the ethernet port.  Kinda odd that you have to pick either-or.  I never got the integrated wireless card working so I just use a USB Linksys one.  It actually makes a neat little netbook...for about an hour until you have to plug it in again!

---

### Post by PortableHuman on 2010-02-02
Hey guys,

I had the *exact* same problem as this with Ubuntu 9.10 and my Acer Travelmate C100. However, for some reason, I kept getting a kernel panic when trying to install from the Desktop CD, so I resorted to the Alternate install. It installed, but still the GRUB Geom Error -- trying to install LILO either afterwards or during the install was unsuccessful -- I still got the GRUB Geom Error if it was installed afterwards, and it came up with an error during the installation process with LILO, saying it couldn't write it to /target/. Unfortunately, I didn't get the exact error written down.

However, I found a simple solution to get Ubuntu 9.10 booting, and I'm posting it here for reference to others. It's just a matter of replacing Grub2 with Grub Legacy, as per this [HowTo]("http://ubuntuforums.org/showthread.php?t=1298932").

Regards,
PortableHuman

---

### Post by frith on 2010-03-25
Okay, seriously this is a bit scary. I was trying to install xubuntu 9.10 on my Acer C100, got this error, googled 'Grub geom error' and found this thread as one of the first results.

I have been using Ubuntu/Linux for about 5 years now, and I have *never* found a thread with the exact problem and solution (down to the same model machine!) with a single search (sure, I've found solutions, but never for the exact same thing I am trying to do).

So I just had to comment and say that the Ubuntu community is nine kinds of awesome! You guys rock!

---

### Post by IntuitiveNipple on 2010-04-05
I've opened a bug report to deal with this issue:

[Bug #555500 Buggy BIOS hard disk workaround missing; causes: "Geom Error"](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/555500)

I'd be grateful if those of you affected could add your comments to that report; specifically the make and model of PC you're using (in case more than the C100 are affected).

As you'll see from my diagnosis in the bug report the cause of the problem is a bug in the BIOS whereby it passed incorrect device details to the boot strap loader.

I'm also working on a fix now the bug in grub-setup has been found.

---

