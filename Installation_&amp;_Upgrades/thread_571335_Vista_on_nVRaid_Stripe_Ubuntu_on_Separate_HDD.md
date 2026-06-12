---
title: "Vista on nVRaid Stripe Ubuntu on Separate HDD"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by JRd1st on 2007-10-09
Here's my situation;
I already had Vista installed on an nVidia Stripe array on 2 WD Raptors.  I then installed Ubuntu Feisty on a seperate HDD from the live CD (I used the AMD 64 version, since I have an X2).

During the install, Feisty never saw my Vista installation, I guess because it's on a RAID setup.  Windows doesn't even see the drive I have Ubuntu on anymore, but I can still boot to either OS depending on which drive I have my boot priority set to.

I've installed ntfs-3g and dmraid.  But Feisty can't mount my RAID.

sudo dmraid -tay gives me;
nvidia_ecfabjce: 0 290451968 striped 2 256 /dev/sda 0 /dev/sdb 0
nvidia_ecfabjce1: 0 290423007 linear /dev/.static/dev/mapper/nvidia_ecfabjce 63


I tried using EasyBCD from Vista, and I can get it to almost start booting; I get a GRUB(?) menu with four Kernel selections plus a memtest selection, but trying to run any of them gives an error something like cannot find file.

What to do?  

I'd prefer using a Vista boot menu, because I intend for it to be my default.

If you have any suggestions, please be explicit.  lol  I've read a lot of posts and, even though I'm pretty good in a Windows environment, I'm n00bish in Linux.  So, mount point, and mount options draw a blank in me.  (I figure ntfs-3g is good for the File System entry.)


Thanks,
JR

---

### Post by dabl on 2007-10-09
Assuming your RAID is a "hardware" RAID (i.e. there is a "brand X" RAID controller chip on your motherboard and a Windows driver for it), you can't use it for Linux.  There's no driver for Linux, so Linux isn't going to "see"it.  :(

---

### Post by JRd1st on 2007-10-09
OK, so how do I get Ubuntu to boot without messing around in my BIOS, all the time.  I don't really need Linux to see or mount the RAID drive, except, maybe to tell a boot loader it's there.  

But, if there's a way to tell the loader on the RAID to run Ubuntu from the other drive, like a boot menu made by EasyBCD, then that's what I really want.

I don't know if my terminology is exactly correct, but you get the idea.

Like I said, I can actually get to a Ubuntu menu, but from there I error out.

Thanks, for the reply, anyway.  :KS

---

### Post by dabl on 2007-10-09
I'm outta my league on this, but I'll speculate that the only workable solution will be in the Vista boot menu domain, not the Linux one, because I don't think Linux can see the MBR behind the hardware RAID.  :(

---

### Post by JRd1st on 2007-10-10
I can't believe there's no solution, to this.  lol  My setup isn't all that unusual.

---

### Post by i22yb on 2007-10-11
I have a 2 disk striped raid array (nvidia nforce) in my system that was formatted under windows with NTFS for games & multimedia.  I just spent the last 2 hours figuring out how to get Ubuntu to access it.  Here is what I did to get it to work:

1)  Installed **dmraid** with synaptic

2)  Created a mount point (I used **/media/raid**).  A mount point is just a directory you create on your linux partition that links to the drive you want to access.

     example to create mount point (run from a console):
     **sudo mkdir /media/raid**

3)  From the console I ran **sudo dmraid -tay**

4)  The first line of output this gives refers to the entire raid array, following lines of output are partitions within the array

     example output from my system:
     nvidia_fibcebja: 0 796593920 striped 2 128 /dev/sda 0 /dev/sdb 0
     nvidia_fibcebja**1**: 0 796588032 linear **/dev/mapper/nvidia_fibcebja** 2048

     what I did from here is to grab the device reference to the specific partition I was trying to access:  **/dev/mapper/nvidia_fibcebja1**  (adding the "1" to the end for the partition #)

5)  Then I edited my fstab file using the device reference from step 4 and the mount point I created in step 2

     console command to edit fstab file:
     **sudo gedit /etc/fstab**

     Line I add to the fstab file (yours may vary):
     **/dev/mapper/nvidia_fibcebja1    /media/raid   ntfs   defaults   0   0**

PRESTO! Now my nvidia nforce raid with NTFS works in Windows & Ubuntu!

My next step is to see if I can get UT2004 Windows & Linux versions to both run from the same folder on my raid array so I don't have to have it installed twice!

I would recommend you stick with Grub for your boot menu, creating a Vista boot menu with a Ubuntu option is much more of a technical nightmare.  Besides, you can set Grub to boot into WIndows by default anyways.

---

### Post by i22yb on 2007-10-11
On a side note - if you want to be able to see/browse your Ubuntu drive from within Windows, download the ext2/ext3 windows driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) 

Vista might give you some compatibility warnings about it, but it should work fine.  It works on my Vista system without problems.

---

### Post by JRd1st on 2007-10-11
Thank you so much!  Now all my problems are solved.

I've decided to just use my motherboard's F8 boot menu instead of either GRUB or Vista Boot to select which OS to run. This way there's no danger of messing up a boot sector or MBR, and it works perfectly regardless of whether I've defragged, imaged, restored,  . . .  whatever.

Now I've just discovered Ubuntu Studio, so I'm sure I'll find another whole nest of issues to keep me occupied.  lol

Once again, thanks!

---

