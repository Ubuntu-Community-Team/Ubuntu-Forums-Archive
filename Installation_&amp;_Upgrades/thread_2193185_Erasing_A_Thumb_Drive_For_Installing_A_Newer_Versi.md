---
title: "Erasing A Thumb Drive For Installing A Newer Version OS"
date: 2013-12-11
forum: Installation &amp; Upgrades
---

### Post by Smallwheels on 2013-12-11
I have a thumb drive with Ubuntu 13.04. I used that to install it on my current machine. It holds 4 GB of data. I want to put an updated version on it. When I go to use the Startup Disk Creator program it has a button to erase the disc. I tried it and it gives an error message. Thus it won't erase the thumb drive. Can somebody tell me how to remove the data on the disc or how to write information over the current data so I can put a newer version of the OS on it? 

Thank you.

---

### Post by mikewhatever on 2013-12-11
...and what's the error message? A copy/paste or even a screenshot won't be too much.

---

### Post by Smallwheels on 2013-12-11
Here you go;

org.freedesktop.UDisks.Error.Failed: Error modifying partition: helper exited with exit code 1: In part_change_partition: device_file=/dev/sdg, start=817127424, new_start=817127424, new_size=823132160, type=0x0c
Entering MS-DOS parser (offset=0, size=4004511744)
MSDOS_MAGIC found
looking at part 0 (offset 0, size 823132160, type 0x00)
new part entry
looking at part 1 (offset 817127424, size 2326528, type 0xef)
new part entry
looking at part 2 (offset 0, size 0, type 0x00)
new part entry
looking at part 3 (offset 0, size 0, type 0x00)
new part entry
Exiting MS-DOS parser
MSDOS partition table detected
containing partition table scheme = 0
got it
Warning: /dev/sdg contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions.
ped_disk_new() failed

---

### Post by SuperFreak on 2013-12-11
Can you use GParted to format the drive?

---

### Post by Smallwheels on 2013-12-11
> **SuperFreak said:**
> Can you use GParted to format the drive?I don't know. How would I do that? Give me instructions and I'll try. Is GParted part of the Ubuntu Software Center?

---

### Post by SuperFreak on 2013-12-11
Yes if it is not installed you can download/install it in the Software Center. Then open it, enter password when asked. Locate the USB thumb drive using the drop down menu in upper right corner, Now right click on the drive partition shown in the bar graph  that is your USB thumbdrive and choose unmount. The right click again and choose format (I think  you could format to FAT 32 which is what Disc creator will do anyway). This is your last chance at this point to make sure you have chosen the right partition, if you have selected your root or home poartition by mistake you are in for  a head ache. If you are certain that you have selected the correct partition chose apply and let it run . It may take a few minutes

---

### Post by ajgreeny on 2013-12-11
I am not sure if a simple format will do the trick and remove all the GPT partition table, which is your main problem.

I think you will need to create a new partition table, which you can also do using gparted with the "Device" menu.  Make a new ms-dos partition table and then a single FAT32 partition using all the space on the disk, and you should then be OK to do the rest of the startup-disk creation.

---

### Post by Smallwheels on 2013-12-11
I found a program called disks by searching for partition in the Ubuntu control center. I opened it and it gave me a visual representation of the thumb drive that I selected. It is a 4 GB drive. The first section says Ubuntu 13.04 amd64 Partition 1 823 MB ISO9660. The second section says Ubuntu 13... Partition 2 2.3 MB FAT. I think this is cut off because this sliver on the visual representation is much smaller in width. The last section says Free Space 3.2 GB and nothing more. 

This tool has an icon with gears. Clicking it opens a drop down menu with several choices. The available choices are Format Disk, Create Disk Image, Restore Disk Image, and Benchmark Drive.

I downloaded GPartEd because when I searched for it in Ubuntu all I found was an html file. 

When I opened GPartEd I got this message which is about the same as the previous message: "Libparted Warning
/dev/sdg contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?"

So is this a GPT partition table? I have no idea. The GPartEd window has this message open waiting for me to click yes or no. 

I see there are a couple of suggestions here. I would like a clarification about why I should choose either method. 

With the Disk program there is the choice of just format disk which I think will take me to another window to choose which format. I haven't clicked it yet so I'm just guessing. Then there is the move partitions around and create new ones suggestion. Maybe both would work. Of course I really don't know how to do that because the GPartEd is stuck awaiting an answer to that Yes or No question. So I don't know what will be on the next screen. 

I really appreciate your knowledge about this situation. I eagerly await your replies.

---

### Post by SuperFreak on 2013-12-11
The method  ajgreeny provided makes the most sense

---

### Post by Smallwheels on 2013-12-11
Thank you SuperFreak. 

I opened GPartEd and selected Device and in the drop down menu selected Create Partition Table. In the next box there was a choice to apply it. It said that the default is to create an MS-DOS partition table. I selected Apply. This brings up a new window labeled Libparted Bug Found!

It says: Partition(s) 1,2 on /dev/sdg have been written, but we have been unable to inform the kernel of the change, probably because it/they are in use. As a result, the old partition(s) will remain in use. You should reboot now before making further changes. 

Then there is s choice of either cancel or ignore. Clicking ignore just takes me back to the GPartEd window and nothing happens. 

Any suggestions?

---

### Post by ajgreeny on 2013-12-11
Make sure the partition(s) on the flash drive are unmounted by right clicking on them and choosing "Unmount".  You can't do anything to any partition that's mounted in gparted.

---

### Post by oldfred on 2013-12-11
Did you make sure it was unmounted before doing anything with gparted? You should see a little key icon next to it if mounted and can right click to unmount.

Did you perchance use the dd procedure to create the hybrid flash drive installer. It is my understanding that does not create a standard partition type install but is more like the ISO. So you need to zero out the MBR, so standard partition tools do not hiccup on invalid partition info.

As with anything dd related make doubly sure you have correct drive, replace X with correct drive letter.
dd if=/dev/zero of=/dev/sdX bs=512 count=1

Also if somehow it really has gpt data.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

---

### Post by Smallwheels on 2013-12-11
I restarted the machine to see what would happen. I opened GPartEd again and did not get the same error messages. I'm now at a screen where I can choose the sizes of the partitions. As I make one larger the second one shrinks. This is set to be a primary partition. What size should I make the first partition? Does it matter if I will be loading an ISO to this so that it is bootable? Should I make the partitions 50/50 in size? I will be loading an OS image which varies from version to version. If I make the main partition just a little bigger than the ISO file would that make the remainder of the disc usable for storing files the same way a regular hard drive would work? This is something I don't really know about.

In the future I do want to put an OS on an external HD and boot it the same way I do the internal HD. It will be a pocket computer I can connect to other machines. Is what I am doing now with this thumb drive sort of the same thing?

---

### Post by Smallwheels on 2013-12-11
> **ajgreeny said:**
> Make sure the partition(s) on the flash drive are unmounted by right clicking on them and choosing "Unmount".  You can't do anything to any partition that's mounted in gparted.
At no time did this partition show anything other than the word unallocated 3.73 GiB. I tried right clicking on it and it has a long list of choices but only two are active, "New" and "information". Even in the list of inaccessible choices there were no unmount choices. I did see mount in that list. Under the Partition tab it says unallocated. Under the File System tab it says unallocated. Under the Used tab there is just a dash. Under the Unused tab there is a dash. Of course this is in GPartEd. The Disk program had those other partition labels that I described. 

So through no skill of my own and only guessing and using deductions I wondered if that word unallocated meant that what I had done had cleared the data off of the drive. To check this I opened the Startup Disk Creator program again. It said 3.8 GB was the size on the drive. I selected erase disc and this time the error message about partitions did not come up. I then selected apply and the drive was ready to receive the new ISO. I selected the file to install using the Startup Disk program and it took a few minutes to load. I have not tried it yet but it did finish loading the files successfully. Now I need to try to boot from it. 

Perhaps fiddling with GPartEd fixed the partitions even though I didn't actually modify anything with that program. That allowed the Disk program to erase the data. Originally that program wouldn't allow me to erase anything. It also said that the data I wanted to write to the drive wouldn't fit into the remaining space on the thumb drive. Of course that was not really true. If you recall my description of the three visual representations of the drive partitions it showed that the last one was over 3 GB in size. Something in these different programs wasn't reading the information correctly. Not all of them could be correct. 

I'm going to try to boot the new drive. I will report the results.

---

### Post by kurt18947 on 2013-12-11
If I'm starting with a new thumb drive or am changing it, I usually open Gparted and delete all partitions then recreate new and format.

---

### Post by Smallwheels on 2013-12-11
I tried to boot from the thumb drive and it failed. I got a message that it read an unknown keyword. This was in just one line that showed up. Below that line there was just Boot: and the underscore cursor just blinked and nothing happened after that. 

Since this failure I have deleted the information on the drive according to Disk utility. I have GPartEd open and it correctly shows two partitions. One is fat32 3.73 GiB with 7.47 MiB used and 3.72 GiB unused. It has Flags saying boot,lba. The other partition is unallocated. 

I clicked the fat32  /dev/sdb1 partition and right clicked the little key symbol and unmounted it. I can right click on the fat32 partition and get the menu choice to delete it. I right click on the unallocated partition and there is no such choice active. The only active choices are New and Information. Is it possible to delete both partitions or is it only possible to work with one? If so how do I create new partitions and format the drive?

---

### Post by SuperFreak on 2013-12-11
If it is unallocated then it is already deleted,
The flags on the partitions may have been a factor interfering with the Live USB, they should disappear when the entire USB is deleted and made into unallocated space.

---

### Post by electrohandyman501 on 2013-12-11
I had issues trying to erase and reuse a thumb drive as well. No matter how I tried to go about erasing/formatting thru any GUI interface, Win 7 or Linux, it wouldn't fly.
I finally ended up with the 'mkfs' thru the command line. After that I could do my 'create bootable usb drive' for live boot.

---

### Post by Smallwheels on 2013-12-20
> **ajgreeny said:**
> I am not sure if a simple format will do the trick and remove all the GPT partition table, which is your main problem.

I think you will need to create a new partition table, which you can also do using gparted with the "Device" menu.  Make a new ms-dos partition table and then a single FAT32 partition using all the space on the disk, and you should then be OK to do the rest of the startup-disk creation.

I opened GPartEd and selected Device. I then selected Create Partition Table. This opened a warning about the data on the drive would be erased if I continued. I did continue. Then I selected the new 3.73 GiB unallocated single partition and right clicked it. There were two choices. New and Information. I selected New. 

A new dialog box opened. It said Create new Partition. At this step I don't know how to proceed. You suggest to create a new MS DOS partition. There is no choice anywhere for me to do that in this box. I see several lines on the left column and three on the right. 

Directly under the graphical illustration of the drive are the words Minimum size 1 MiB   Maximum size: 3,818 MiB

The left column has:

Free space preceding (MiB) and a box with the number 1 and an up and down arrow.

New size (MiB) and a box with the number 3818 with an up and down arrow.

Free space following (MiB) and a box with 0 and an up and down arrow.

Align to: and a box with MiB with an up and down arrow. The choices in this box are Cylinder, MiB, and None. I don't know what this means at all. 

The right column has these;

Create as: and a box with an up and down arrow to select Primary Partition or Extended Partition. The choice of Logical Partition is unavailable.

File system: (The choices are: ext2, ext3, ext4, fat16, fat32, linux-swap, ntfs, unformatted)

As I've said earlier I want to put a bootable iso on this 4 GB thumb drive. This will be a live version for me to try and perhaps load if I like the new version. 
What is my next step? How do I allocate space on this drive to accomplish my task? 

I don't really understand the needs of the Free space preceding/New size/Free space following/ and Align to, choices. 

I think what I'm doing requires this to be a primary partition and to be formatted in FAT 32. I can choose whatever name I want for the Label box on the right side of the dialog box. 

The raw CD image size is 729.8 MB. I don't know how big it will be when loaded onto the thumb drive.

So what's next for me to do?

Thanks for your help.

---

### Post by Dennis N on 2013-12-20
To use the USB as an install medium and live OS, leave all the left side choices you see as they are. On the right side, choose Primary partition, then File System: fat32. Leave Label blank. Click ADD. Finally, back on the main screen, click the clockwise-pointing arrow (tooltip says: apply all operations) on the tool bar to complete the job. Now you can use the stick with unetbootin to make a live USB/installer.

---

### Post by Smallwheels on 2013-12-20
> **Dennis N said:**
> ...Finally, back on the main screen, click the clockwise-pointing arrow (tooltip says: apply all operations) on the tool bar to complete the job. Now you can use the stick with unetbootin to make a live USB/installer.Where is the clockwise arrow? I click Add and the underlying dialog box is now viewable with the graphical partition now surrounded by green. The single partition is listed in the column. There are no clockwise arrows on this page. The only items that can be selected on the tool bar are "Undo Last Operation" and "Apply All Operations". 

I selected Apply All Operations. Then a box opened with a progress bar. When it was completed the box disappeared. The main page opened again and the tool bar options changed. Now the only ones that are functional are "Delete the selected partition" and "Resize/Move the selected partition". I guess it's done. 

Did I miss something by not finding that clockwise arrow?

---

### Post by Dennis N on 2013-12-20
Well, I guess it depends on the version of gparted if the arrows are there or not. Mine has the clockwise and counter-clockwise arrows to Undo Last Operation and Apply All Operations, but you can also do the same from the menus. Anyway, you made the correct choice. You are done preparing the USB.

---

### Post by cybrsaylr on 2013-12-20
Disk Utility, found in all Ubuntu versions now I believe, also has options to format drives.

---

### Post by Smallwheels on 2013-12-21
So what does this stuff mean?> **Smallwheels said:**
> 
Directly under the graphical illustration of the drive are the words Minimum size 1 MiB   Maximum size: 3,818 MiB

The left column has:

Free space preceding (MiB) and a box with the number 1 and an up and down arrow.

New size (MiB) and a box with the number 3818 with an up and down arrow.

Free space following (MiB) and a box with 0 and an up and down arrow.

Align to: and a box with MiB with an up and down arrow. The choices in this box are Cylinder, MiB, and None. I don't know what this means at all. 

The right column has these;

I don't really understand the needs of the Free space preceding/New size/Free space following/ and Align to, choices. 


---

### Post by sudodus on 2013-12-21
@*Smallwheels*,

If you still have problems, I suggest that you try some other method.

0. Did you check with ***md5sum*** that the iso file was downloaded in a correct way?

1. Check some links at the internet to get information about methods and tools to create thumb drive for installing an OS from an iso file.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073") - ***mkusb***

2. The Ubuntu Forums Tutorial page [One Button Installer, 'OBI']("http://ubuntuforums.org/showthread.php?t=2172971") and Ubuntu wiki page [https://wiki.ubuntu.com/phillw/OBI](https://wiki.ubuntu.com/phillw/OBI) describe a new method to install an Ubuntu flavour or Ubuntu based operating system.

*. If you use mkusb or the OBI, you need not erase the thumb drive.

---

### Post by kurt18947 on 2013-12-21
> Where is the clockwise arrow? I click Add and the underlying dialog box  is now viewable with the graphical partition now surrounded by green.  The single partition is listed in the column. There are no clockwise  arrows on this page. The only items that can be selected on the tool bar  are "Undo Last Operation" and "Apply All Operations". 

I selected Apply All Operations. Then a box opened with a progress bar.  When it was completed the box disappeared. The main page opened again  and the tool bar options changed. Now the only ones that are functional  are "Delete the selected partition" and "Resize/Move the selected  partition". I guess it's done. 

Did I miss something by not finding that clockwise arrow?

I suspect the arrow shape has to do with themes and icon sets

> Directly under the graphical illustration of the drive are the words Minimum size 1 MiB   Maximum size: 3,818 MiB

The left column has:

Free space preceding (MiB) and a box with the number 1 and an up and down arrow.

New size (MiB) and a box with the number 3818 with an up and down arrow.



I believe -not certain - that current versions of gparted leave 1 MB. free space before a file system to insure proper alignment with 4k blocks/Advanced Format.  It looks like your flash drive is ready to install a live USB using Startup Disk Creator(included), Unetbootin (repository) or similar.

---

### Post by Smallwheels on 2013-12-23
I used Unibootin this time. Though it wasn't as straightforward as I had hoped, it worked out. It seems that the graphical interface is really archaic. 

I loaded the Ubuntu based OS called Trisquel. It is recommended by the Free Software Foundation because it has no proprietary software. It has a big flaw for me. It doesn't work with my WiFi so I guess I won't be using it. 

Ubuntu is really great. It has just about everything I want (with tweaks). The one thing it has that I wish it didn't is proprietary software. I just want to have an OS that is so open that the community can notify us if the government plugs in spyware. I'm sticking with Ubuntu for now. I like Unity. I just need more RAM to run it. One good thing I can say about my trial with Trisquel, it was FAST!  

I won't give up seeking a free software distribution that works with my hardware. It probably won't be too long before there are drivers for everything so that a free OS has everything it needs to do everything in a free way.

---

### Post by sudodus on 2013-12-23
If Ubuntu works with your hardware, the other flavours Lubuntu, Xubuntu, Ubuntu Gnome, Kubuntu, ..., of the same version (12.04 LTS or 13.10) are very likely to work, because there is the same engine under the hood. Only the desktop environment and some tweaks differ.

Lubuntu has the lightest foot-print followed by Xubuntu. They will probably work well without more RAM, but if you like Unity, keep it and get more RAM :-)

---

