---
title: "Dualboot Meerkat/Win7 OEM preinstalled..."
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by MudOilnGears on 2011-03-05
Hello!
I have a question here for you people. I just bought an HP ProBook, it hasn't arrived yet, but should around Monday. My question is this. Can I install Ubuntu aditionally without fear of frying Win7 in the process? According to Lifehacker it is possible, altho I'm not sure he is referring to an OEM installation. Also that article leaves out the swap partition,I do not know how good/bad that idea is. If I mess up, the restore disk will not allow me to do a full install, right?
Where do I start (aside from burning my restore disks, and backing everything else up)?
Thanks in advance
HJM

---

### Post by jeremyjjbrown on 2011-03-05
If you are careful and follow a good guide you should have no issues installing Ubuntu. There are several ways to do it. The easiest and most risk free is with the WUBI installer. If you have not tried out Linux before I would do it this way the first time.

If you want, google for a guide to install and post it here and I can take a peak at it to make sure it's cool.

---

### Post by Hedgehog1 on 2011-03-06
If I might add to **jeremyjjbrown** suggestions:

Please burn a Windows recovery CD and backup the Windows system to DVDs before you do anything else.  There are tools in Win7 for these tasks.

This will give you a recovery point for anything that might go wrong in the future (and may have nothing to do with an Ubuntu install, even).

An once of prevention....

***The Hedge***

:KS

---

### Post by MudOilnGears on 2011-03-06
I use linux right now on a desktop. It is on a separate drive from XP tho. I must admit I unplugged the WIndows drive when I installed ;)

Here are two links...
[http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/#!5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

[http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/](http://www.howtogeek.com/howto/9059/dual-boot-your-pre-installed-windows-7-computer-with-ubuntu/)

Altho in both cases they are using older versions of Ubuntu, but I imagine the main installer is similar.
[http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/](http://www.wonderhowto.com/how-to-dual-boot-ubuntu-10-10-and-windows-7-side-by-side-0123943/)
This one seems to be better, but he assumes I have an empty partition already, which I don't.
You might wonder why I ask if there are so many writeups out there, but I prefer to get assistance from you guys on here, than just blindly follow a writeup and fry something.

To "TheHedge" You may be sure I will burn those disks first thing!

---

### Post by Hedgehog1 on 2011-03-08
> **MudOilnGears said:**
> 
... To "TheHedge" You may be sure I will burn those disks first thing!

Excellent to hear!

Here are some before/after pictures of a dual boot:

Before Ubuntu added (from Windows 7):
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/4036144.png[/IMG]

Before Ubuntu added (from Gparted on LiveCD):
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/129938.png?500[/IMG]

After Ubunutu added as dual boot (from Ubuntu Disk Utility):
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/1089227.png?500[/IMG]

After Ubunutu added as dual boot (from Windows 7):
[IMG]http://ubuntuhedgehog.weebly.com/uploads/6/4/4/9/6449410/6488186.png?500[/IMG]

This install is on a little 40 gig virtual box; but it shows what changes happen to your hard drive when you install dual-boot.

***The Hedge***

:KS

---

### Post by Jose Catre-Vandis on 2011-03-08
My advice is to resize the big windows partition WITHIN Windows 7 using the Computer Management module, prior to booting up with an Ubuntu Live CD or ALT CD. Windows 7 can be a bit peculiar about having its partitions resized by third parties. After that its plain sailing :)

---

### Post by MudOilnGears on 2011-03-08
Thanks all,
I see I have the a main 280Gb partition, a 2Gb partition, and when I was burning the system image I see there is a partition called HP RECOVERY. 
So long as I resize the large partition from Windows, and don't touch the other two I should be OK?

---

### Post by Jose Catre-Vandis on 2011-03-08
That's right :)

So in Windows open up Computer Management, resize the big windows partition, and when that's done, just leave the unallocated space as it is, and reboot with your Ubuntu CD in place.

Make sure you say yes to installing grub to the MBR, and with any luck you'll get a choice of Ubuntu or Windows to boot from when all is done. If not, pleanty of help on the forum for getting Windows back.

---

### Post by Mark Phelps on 2011-03-08
> **MudOilnGears said:**
> Thanks all,
I see I have the a main 280Gb partition, a 2Gb partition, and when I was burning the system image I see there is a partition called HP RECOVERY. 
So long as I resize the large partition from Windows, and don't touch the other two I should be OK?

Take another look -- this time, using the Disk Management function in Win7.  Make sure that you do NOT actually have four partitions.  There's likely to be a fourth one there, a small one, possibly labeled System Reserved or something like that.

The problem you run into with such a partition setup is that when you go to make another partition, Windows asks you if you want to convert your existing partitions into Dynamic Disks -- something you do NOT want to do.  And, if you do the partition creation outside of Windows, when you then boot back into Windows, it does the conversion for you automatically.

So, don't just go blindly charging ahead creating another (possibly fifth) partition.

---

### Post by MudOilnGears on 2011-03-08
> **Mark Phelps said:**
> Take another look -- this time, using the Disk Management function in Win7.  Make sure that you do NOT actually have four partitions.  There's likely to be a fourth one there, a small one, possibly labeled System Reserved or something like that.

The problem you run into with such a partition setup is that when you go to make another partition, Windows asks you if you want to convert your existing partitions into Dynamic Disks -- something you do NOT want to do.  And, if you do the partition creation outside of Windows, when you then boot back into Windows, it does the conversion for you automatically.

So, don't just go blindly charging ahead creating another (possibly fifth) partition.

Oh the wisdom of those who have been there before ;)
I did a LiveCd boot just a bit ago before seeing this post, ran fdisk -l and got 4 partitions, and a teeny tiny unallocated bit. I just thought it was an aditional partition, I didn't know it could affect anything.

```
 
root@ubuntu:/home/ubuntu# fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a6dc38b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          39      307200    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              39       36695   294440960    7  HPFS/NTFS
/dev/sda3           36695       38653    15728640    7  HPFS/NTFS
/dev/sda4           38653       38914     2092376    c  W95 FAT32 (LBA)
root@ubuntu:/home/ubuntu# 


```What do I do in this case after shrinking the sda2 partition to create unallocated space? How do I prevent this "conversion"?
Thanks for the warning, got me in time ;)

---

### Post by Hedgehog1 on 2011-03-09
> **MudOilnGears said:**
>  
```
 Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a6dc38b
 
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          39      307200    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              39       36695   294440960    7  HPFS/NTFS
/dev/sda3           36695       38653    15728640    7  HPFS/NTFS
/dev/sda4           38653       38914     2092376    c  W95 FAT32 (LBA) 
```
 
MudOilnGears,
 
You are allowed 4 primary partitions on a hard drive. This new PC has used all four (Numbers sda1-sda4) already used. To add more partitions, an exsisting partition must be deleted.
 
/dev/sda2 is your boot partition (leave thisone alone!!)
/dev/sda4 carries your Windows restore disks.
 
Do you know what data is on /dev/sda3? If it is an 'empty' windows 'D:' drive, we can play some games with it.
 
Please determine if /dev/sda3 could be converted into a a logical partition. Is so, you can shink /dev/sda2, delete /dev/sda3, create a ned logical /dev/sda3, and put /dev/sda5 in it as your ubuntu parition and /dev/sd6 in it as your swap partition.
 
Like this:
|sda1|--------sda2--------|---------------sda3----------------|-sda4--|
|sda1|--------sda2--------|-----------sda5-------------|sda6|-sda4--|
 
 
***The Hedge***
 
:KS

---

### Post by MudOilnGears on 2011-03-10
I see, let me post a screenshot here if I can...
[IMG]https://picasaweb.google.com/lh/photo/o01YUQgmC6ZPqK3kwvlQKg?feat=directlink[/IMG]

sda3 is HP RECOVERY
I don't know if this screenshot will work, but I'll try.
Thanks a million!

I see the image did not work, here is the direct link
[https://picasaweb.google.com/lh/photo/o01YUQgmC6ZPqK3kwvlQKg?feat=directlink](https://picasaweb.google.com/lh/photo/o01YUQgmC6ZPqK3kwvlQKg?feat=directlink)
[IMG]https://picasaweb.google.com/lh/photo/o01YUQgmC6ZPqK3kwvlQKg?feat=directlink[/IMG][IMG]https://picasaweb.google.com/lh/photo/o01YUQgmC6ZPqK3kwvlQKg?feat=directlink[/IMG]

---

### Post by MudOilnGears on 2011-03-10
Ok, got the screenshot to work now.
[IMG]http://i916.photobucket.com/albums/ad6/MudOilnGears/screenshot.png?t=1299805485[/IMG]

---

### Post by Hedgehog1 on 2011-03-10
Posting graphics is a hoot, huh?

So we want something like this:
|sda1|--------sda2--------|---------------sda3----------------|-sda4--|
|sda1|--------sda2--------|-----------sda5-------------|sda6|-sda4--|

If you are willing to sacrifice your HP_RECOVERY partition, then you can install Ubuntu.

You would boot off the live CD, select 'try' and run GNOME Partition Editor (gparted for short) off the System >> Administration menu.

In gparted, delete **sda3**.

Once deleted, add **sda3** in again, but make it an extended partition.

Then create a 13 gig **sda5** partition (format: ext4) and use the rest of the extended partition as Linux Swap (**sda6**).

Let gparted do it's thing, exit out, and run install.

Choose the manual configuration method, and set the **sda5** to '/' and the **sda6** to 'swap'.  **sda5** can also be set to be the place to install grub.

**[SIZE="3"]Clear as mud, right?[/SIZE]**  It is really easy the third time you install. :D

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-11
I have just created a virtual machine and set it up like the HP install.

I will take screen shots and post the steps as I go.  First how it looks in Windows:

[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-11
What it looks like in gparted off the LiveCD:

[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-11
Right click on sda3 and select 'Delete':

[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-11
Press the 'check' mark button to really make the change:

[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-11
Right Click, on empty area, select new and create extended sda3:

[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]

Press that check mark button again...

---

### Post by Hedgehog1 on 2011-03-11
Create you sda5 Ubuntu partition, leave a little room for swap later:

[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]

Format this ext4 - and press that check mark button again.

---

### Post by Hedgehog1 on 2011-03-11
Create sda6 and make it swap space:

[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]

Press the check mark button again, and you get this:

[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]

And you are ready for to install Ubuntu.

---

### Post by Hedgehog1 on 2011-03-11
Select this during the install:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

And you will get to here:

[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]

We will add some extra data to sda5 and sda6.

---

### Post by Hedgehog1 on 2011-03-11
With sda5 highlighted, press the [CHANGE] button:

[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]

These settings prepare the partition to be exdt4, '/'.

---

### Post by Hedgehog1 on 2011-03-11
Repeat the steps for the swap area:

[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]

This usually set itself up OK.

---

### Post by Hedgehog1 on 2011-03-11
[SIZE="4"]LAST STEP[/SIZE]

You are ready to install.  Press [Install Now].

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

---

### Post by Hedgehog1 on 2011-03-11
Final Reference. What the drive looks like in the 'Disk Utility' on Ubuntu after the load is complete:

[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  



Feel free to post, mock me, whatever.

***The Hedge***

:KS

---

### Post by MudOilnGears on 2011-03-11
Great writeup man!
Thanks a million!
So my options are
A: Offer up my recovery partition on the altar to install Ubuntu
B: Not offer it up and stay with Windows 7

What are the odds I'm going to need it? I already burned my system image and windows repair CD as per your suggestion.

I think I shall probably choose A: I've been running Windows machines with no system disk anyway for a long time...

---

### Post by MudOilnGears on 2011-03-11
On the images, what happened was I was trying to use a Picasa web album, needeless to say it didn't work ;) Using Photobucket now...

---

### Post by MudOilnGears on 2011-03-11
One detail I forgot to ask.
I currently have 2GB of RAM, but plan to upgrade to 4GB in the future. Should I make the swap partition 4GB right away, or doesn't it make a difference?
Thanks...

---

### Post by Hedgehog1 on 2011-03-11
Swap Space;

If you will use Sleep/Hibernate, then creating a 4.4 gig swap now for the future 4 gig ram is a good idea.

I have 12 gigs of RAM and a 28 gig swap space, and I never use hibernate or sleep.  It has turn out to be a waste of disk space, but since I have 600 gigs still open on the drive I have not messed with it (not yet).

Now, you don't have to sacrifice the *sda3*, you can sacrifice **sda4** (HP_TOOLS) and shrink **sda2** and move **sda3** over.

I just chose the most 'easy to document' option.

***The Hedge***

p.s. HP used the 'HP-RECOVERY' partition instead of shipping disks.  Once you have a good set of disks made, the value of the partition is much less.  If you are concerned, make a second set of disks 'just in case', then nuke **sda3** and go for it.

:KS

---

### Post by MudOilnGears on 2011-03-11
HP_Tools has some kind of BIOS stuff in it, probably to update BIOS? I don't really know, so I'd rather slaughter Recovery, since it has enough space for what I need without touching another partition. That is, unless the HP_TOOLS is less necessary than RECOVERY.
Basically so long as I have a good set of disks I don't need the RECOVERY partition?
I think I have tomorrow afternoon planned ;)

---

### Post by Hedgehog1 on 2011-03-11
MudOilnGears,

I agree that with a good set of recovery disks (or two sets if you want to be extra sure), sacrificing **sda3** is simplest and safest.

If the day comes that you need more space for Ubuntu, we can walk you through the:

1) Shrink **sda2** using Windows Disk Management
2) Move/Resize **sda3** extended partition using gparted
3) Move/Resize **sda5** Ubuntu partition using gparted

And you will have more Ubuntu space!

But lets burn that bridge when we get to it...

***The Hedge***

:KS

---

### Post by MudOilnGears on 2011-03-11
Thanks, I was looking at the HP_TOOLS partition, it seems that one is for the "QuickLook" utility which is to store contact info .etc without having to boot up, I'd rather not touch that. I'll probably go for RECOVERY.
That way I can work without that partition without resizing anything else. 15Gb is more than enough for me right now... BTW on which is GRUB supposed to be installed?
Thank you, looking forward to tomorrow afternoon, and hoping I don't fry something ;)

---

### Post by Hedgehog1 on 2011-03-12
Grub will be physically installed following the '/' path (**sda5** in your case).

The boot loader goes the the 'default' location if you leave that option alone (**Device for boot loader installation**):

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

Using the default makes it easiest because **sda1** stays the boot partition at all times, no matter what:

[IMG]http://img269.imageshack.us/img269/2134/hp4partitions15o.png[/IMG]

***The Hedge***

:KS

p.s. Using a virtual machines to do test runs and make screen shots is just awesome.  I had not removed the HPWin7 Vbox image, so I was able to fire it right up and take another screen shot.  So cool. *** Hedgehogs really like cool.***

---

### Post by MudOilnGears on 2011-03-12
Ok, so I'll let the installer take care of that, if it doesn't pick up windows right away, I'll come back here ;)
If hedgehogs like cool,then hedgehogs *are *cool, and I like cool...

---

### Post by MudOilnGears on 2011-03-12
Well,here I am posting from a finished Maverick Meerkat install! Hurray for the hedgehog!
Grub picked up Win7 right away, but put itself first, just like I wanted it.
Thanks for the screenshots, I kept switching between your posts and the installer, try that with Windows ;)
Again, a big thank you, what would the world be like if everyone kept his knowledge to himself?
Thank You

---

### Post by Hedgehog1 on 2011-03-12
Preparations are being made here for the '**hedgehog happy dance!**' to celebrate your success!

*First I gotta move all the furniture, and then I have a CD around here somewhere...*

The next fun things will be giving more of your disk space to Ubuntu.  That will be easy.  **Really.**

***Where IS that CD?!?!?***

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-12
> **MudOilnGears said:**
> 
Thanks for the screenshots, I kept switching between your posts and the installer, try that with Windows ;)


Hey, not so loud!  Soon every one will want Ubuntu...  Oh, wait... Never mind.

---

### Post by XsheepX on 2011-03-12
I dual-booted win7 with Ubuntu 10.10 for like 4 months, and I only have one warning for you:
Do **not** edit your partitions or anything regarding your hard drive in Windows! If you do, GRUB will have an error and will prevent you from accessing your Operating Systems.

tl;dr, only edit your partitions in Ubuntu or GRUB will go haywire.

---

