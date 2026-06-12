---
title: "manual partition help"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by ltuscany on 2008-01-12
I'm looking to dual boot my laptop with XP and ubuntu but the only options I have from the partitioner is guided-entire disk and manual.  This is my first time installing linux (or re-partitioning for that matter) and i'm just not sure the steps I need to take get everything up and running.

I have a 100 gig hard drive with about 40 gigs of free space on it, so I would like to split that up into 75 for windows and 25 for linux.  I already have everything backed up and defragged too.

thanks, lt.

---

### Post by Pumalite on 2008-01-12
Go Manual and do this:
10 GB for '/'
2x RAM up to 1 GB for /swap (except laptops where /swap should equal RAM)
The rest for /home

---

### Post by ltuscany on 2008-01-12
> **Pumalite said:**
> Go Manual and do this:
10 GB for '/'
2x RAM up to 1 GB for /swap (except laptops where /swap should equal RAM)
The rest for /home

Where am I going to do this?  Do I click on 'New Partition Table'?  And how much space does that give me for windows and linux with these numbers, i was looking for about 20 gigs to be used for my linux partition

(Also I have 1GB of Ram)

---

### Post by ltuscany on 2008-01-12
[IMG]http://i75.photobucket.com/albums/i301/ltuscany/Screenshot-1.png[/IMG]

---

### Post by Pumalite on 2008-01-12
From your Live CD, post:
sudo fdisk -lu

---

### Post by ltuscany on 2008-01-12
If you click on 'New Partition table'  this message comes up:

You have selected an entire device to partition. If you proceed with creating a new partition table on the device, then all current partitions will be removed.

Note that you will be able to undo this operation later if you wish.

Then I can 'continue' or 'go back'

---

### Post by ltuscany on 2008-01-12
My goal with this is to avoid reinstalling windows so I just want to be careful.


ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      112454       56196   de  Dell Utility
/dev/sda2   *      112455   187478549    93683047+   7  HPFS/NTFS
/dev/sda3       187478550   195366464     3943957+  db  CP/M / CTOS / ...

---

### Post by Pumalite on 2008-01-12
What do you have in sda3?

---

### Post by ltuscany on 2008-01-12
Honestly I really have no idea, my best guess would be a system restore point but I'm not sure.

---

### Post by ltuscany on 2008-01-12
[IMG]http://i75.photobucket.com/albums/i301/ltuscany/Screenshot-2.png[/IMG]

---

### Post by Pumalite on 2008-01-12
Use Gparted Live CD to extend/resize your partitions so you'll have a new partition for Ubuntu. sda3 is too big to be a restore point. I suspect is 'empty' space. Maybe you can use it too.
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Read the manual.

---

### Post by c0met on 2008-01-12
When I install Ubuntu, I prefer to partition my disk manually with GParted before I install the OS. To do this, I perform the following steps.

[LIST]
[*]Boot from the LiveCD
[*]Go to [COLOR="DarkRed"]**System >> Administration >> Gparted**[/COLOR]
[/LIST]
If you have a non-partitioned hard drive, you should now see a partition called something like **[COLOR="Purple"]sda[/COLOR]** or[COLOR="Purple"]** hda**[/COLOR]
[LIST]
[*]right click on the partition
[*]choose resize
[*]drag the right side of the partition until it shows that you have a 75 GB partition (this will be Windows and it should have a shaded section on the left showing where your Windows files are. DO NOT RESIZE THE PARTITION ON THE SIDE WHERE YOUR WINDOWS FILES ARE as you could lose your Windows installation.)
[*]choose apply changes (it is possible that GParted will close down with this step. It's ok if it does as it writes the changes before shutting down. Simply restart GParted.)
[/LIST]
You should now have 25 gigs unallocated. Pumalite's suggestion of splitting these 25 gigs into 3 partitions is a good one. To this...
[LIST]
[*]right click on the unallocated space and create a new, [COLOR="DarkRed"]**EXT3 partition**[/COLOR]
[*]resize this partition to (say) 9 MB (during the install process, we'll make this [COLOR="DarkRed"]**/**[/COLOR])
[*]apply the changes (note, you can create all the partitions in a single go and then &#8220;apply&#8221; the changes at the end. I guess I just tend to do it one step at a time.)
[/LIST]
You'll now have 16 GB of unallocated space
[LIST]
[*]right click on the unallocated space and create a 15 GB, [COLOR="DarkRed"]**EXT3 partion**[/COLOR] (during installation this parition will become [COLOR="DarkRed"]**/home**[/COLOR])
[*]right click on the remaining 1 MB and use it all to create a [COLOR="DarkRed"]**SWAP partition**[/COLOR]
[/LIST]
When this is all done, click on the **[COLOR="Purple"]Installation[/COLOR]** icon.

When you get to the screen asking about partitioning your hard drive, choose [COLOR="Purple"]**Manual**[/COLOR]

You should now see, all the partitions listed your earlier post shows. double-check that the types are [COLOR="Purple"]**EXT3**[/COLOR] (for the 9 MB and 15 MB ones) and [COLOR="Purple"]**SWAP**[/COLOR] for the 1 GB one

right click on the 9 GB partition and choose to edit the partition; use the drop-down box to set the mount point to &#8220;/&#8221;
right click on the 15 GB partition and edit it; use the drop-down box to set its mount point to &#8220;/home&#8221;
if the 1 MB partition is not set to SWAP, you can right click on it and use the drop down box to now set it.
make sure that the &#8220;format&#8221; check box is set for the &#8220;/&#8221; partition
you should now be set to install the program

A word of advice, when you get to around 82%, the installation will seem to stall. If you are connected to the internet (which is the preferred option), at 82% the installation process will download repository files from servers and this can take a while. So just be patient.

---

### Post by Pumalite on 2008-01-12
Gparted Live CD is a newer version, more flexible and more powerful, giving also more control. It also works with unmounted drives; essential to partition without problems. I recommend it.

---

### Post by ltuscany on 2008-01-12
> **c0met said:**
> When I install Ubuntu, I prefer to partition my disk manually with GParted before I install the OS. To do this, I perform the following steps.

[LIST]
[*]Boot from the LiveCD
[*]Go to [COLOR="DarkRed"]**System >> Administration >> Gparted**[/COLOR]
[/LIST]
If you have a non-partitioned hard drive, you should now see a partition called something like **[COLOR="Purple"]sda[/COLOR]** or[COLOR="Purple"]** hda**[/COLOR]
[LIST]
[*]right click on the partition
[*]choose resize
[*]drag the right side of the partition until it shows that you have a 75 MB partition (this will be Windows and it should have a shaded section on the left showing where your Windows files are. DO NOT RESIZE THE PARTITION ON THE SIDE WHERE YOUR WINDOWS FILES ARE as you could lose your Windows installation.)
[*]choose apply changes (it is possible that GParted will close down with this step. It's ok if it does as it writes the changes before shutting down. Simply restart GParted.)
[/LIST]
You should now have 25 megs unallocated. Pumalite's suggestion of splitting these 25 megs into 3 partitions is a good one. To this...
[LIST]
[*]right click on the unallocated space and create a new, [COLOR="DarkRed"]**EXT3 partition**[/COLOR]
[*]resize this partition to (say) 9 MB (during the install process, we'll make this [COLOR="DarkRed"]**/**[/COLOR])
[*]apply the changes (note, you can create all the partitions in a single go and then &#8220;apply&#8221; the changes at the end. I guess I just tend to do it one step at a time.)
[/LIST]
You'll now have 16 MB of unallocated space
[LIST]
[*]right click on the unallocated space and create a 15 MB, [COLOR="DarkRed"]**EXT3 partion**[/COLOR] (during installation this parition will become [COLOR="DarkRed"]**/home**[/COLOR])
[*]right click on the remaining 1 MB and use it all to create a [COLOR="DarkRed"]**SWAP partition**[/COLOR]
[/LIST]
When this is all done, click on the **[COLOR="Purple"]Installation[/COLOR]** icon.

When you get to the screen asking about partitioning your hard drive, choose [COLOR="Purple"]**Manual**[/COLOR]

You should now see, all the partitions listed your earlier post shows. double-check that the types are [COLOR="Purple"]**EXT3**[/COLOR] (for the 9 MB and 15 MB ones) and [COLOR="Purple"]**SWAP**[/COLOR] for the 1 MB one

right click on the 9 MB partition and choose to edit the partition; use the drop-down box to set the mount point to &#8220;/&#8221;
right click on the 15 MB partition and edit it; use the drop-down box to set its mount point to &#8220;/home&#8221;
if the 1 MB partition is not set to SWAP, you can right click on it and use the drop down box to now set it.
make sure that the &#8220;format&#8221; check box is set for the &#8220;/&#8221; partition
you should now be set to install the program

A word of advice, when you get to around 82%, the installation will seem to stall. If you are connected to the internet (which is the preferred option), at 82% the installation process will download repository files from servers and this can take a while. So just be patient.


Alright, I tried booting from the gparted live cd and made it to where you determine the new size of the partition.  However,  I did not see anything that might indicate where the windows files were inside the partition and I could not drag anything to change the size.  Have any of you used this program and experienced this or am I just missing something?

I'd also assume you meant gigs and not megs in your post right?

---

### Post by zipperback on 2008-01-12
Might I suggest a couple of detailed howto pages for you.

[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

On that page I have listed a few pages which should resolve the issue for you.

- zipperback
:popcorn:

---

### Post by Pumalite on 2008-01-12
And check this too:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by c0met on 2008-01-12
woops! 

Yes, I did mean Gigs and not Megs - I'll see if I can edit that correction into my post. I notice that people have given you a couple of great links. One that might also be worth investigating is 

[http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/")

I have found this site to be really helpful.

---

### Post by ltuscany on 2008-01-12
[IMG]http://manual.sidux.com/lib/images-en/gparted-en/gparted-2-main-3-en.png[/IMG]

This is where I was getting stuck, when I got to this point the max and min sizes were the same and nothing could be adjusted.  Just seems a little odd.

---

### Post by c0met on 2008-01-12
From what you have posted, I can't see your Windows partition. The partitions that you have listed total around 30 gigs and not the 100 gigs that you said you had.

On what partition is Windows?

---

### Post by ltuscany on 2008-01-12
sorry, should have made it more clear but this is just a screen shot i found on the web as i've been troubleshooting this.

---

### Post by Pumalite on 2008-01-12
Have you read the Manual for Gparted?

---

### Post by ltuscany on 2008-01-12
> **Pumalite said:**
> Have you read the Manual for Gparted?

yes, i went through it when i was eating dinner.

---

### Post by c0met on 2008-01-12
Ahhh :) 

I panicked a bit on your behalf because I thought you might have deleted Windows! 

On the picture that you posted, the yellow shaded area is indicating the region in which files are being used. The dashed-line region is indicating which partition has been selected. Since you have only a single partition, you should see a single partition with are (yellow?) shaded region on the right - much like the picture you posted. From what you have said, this shading should be a bit more than half of the partition's size. On the right side should be white - indicating unused space.  

You need to right-click on the partition and choose, "Resize". If you look at the picture you posted, you can see black triangles at each end of the partition. These are the resizing arrows that I was talking about earlier. It is also possible to simply type in the partition's size.

If you want a 75 GB partition, you need to have..

Free Space Preceeding = 0
Free Space Following = 25000 (since the units for partitions are in megs)

The above setting should set your Windows parition to around 75000 (indicating 75,000 MB or 75 GB)

See if that helps.

[COLOR="Red"]**REMEMBER**[/COLOR], it is not until you click on "APPLY" that changes are made. If in doubt, avoid applying anything because data can be lost if you are unsure.

---

### Post by Pumalite on 2008-01-12
Backing up everything should always be done before the installation of any new OS as a matter of good practice. Make sure you know exactly what you have and where; that way you will know what partition to resize and in what direction.

---

### Post by ltuscany on 2008-01-12
I just tried gparted again and i faced the same problem, i'm unable to adjust how big i want to set my windows partition.  then i didn't notice this until this second time around but in the main window that lists all of the partitions it has my a triangle with a '!' inside it and the amount of space that is used and unused it just blank, under the field tab it just says 'boot'

---

### Post by c0met on 2008-01-12
I do not know exactly what it means but my experience tells me that the ! sign in a triangle could indicate that the drive is somehow locked or protected. Do you run McAfee or some other virus scanner in Windows that might do this?

---

### Post by ltuscany on 2008-01-12
ahh, didn't even think about that.  i'm running symantec anti virus and norton, this also might explain why i'm not seeing the guided-resize that comes with the ubuntu live cd.

---

### Post by c0met on 2008-01-12
Yes, it could be. It might be worth investigating that. I don't know for sure, but it seems that some antivirus software can protect the hard drives quite aggressively - which is what you want, I guess! One of the good things about Linux is that there's not too many viruses to worry about.

Let me know if Norton did stop you, I am interested to find out.

---

### Post by ltuscany on 2008-01-12
well no luck so far with my anti virus stuff and everything from nortons help page about disk partitioning refers you to their partition magic program (BTW its $70) so i'm not quite sure where to go from here.  has anyone else heard of this problem before?

---

### Post by c0met on 2008-01-13
Hmmm.... 

I have no more ideas. Sorry. I have investigated the idea of rootkits and whether or not Norton uses Host (or Hidden) Protected Areas (HPA) to maintain control of systems but I have not had any luck. Interestingly, a 2006 version of Norton Recycler did use HPAs.

Good luck! If you get an answer to your dilemma, please post it here because I'd love to know the outcome :)

Best wishes,

---

### Post by ltuscany on 2008-01-13
after some more investigating i think gparted won't let me resize my partitions because i have bad sectors on my hard drive.  then from what i've read this means my HD is probably going to take a sh!t soon so the plan for now is to clone my hard drive onto a new one and then retry the linux installation.

thanks to everybody for the help.

---

