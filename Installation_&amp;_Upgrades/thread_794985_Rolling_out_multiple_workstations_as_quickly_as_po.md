---
title: "Rolling out multiple workstations as quickly as possible"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by w1z4rd on 2008-05-15
Hi all,

Basically the situation is this. Our ICT company has decided that it can now use Ubuntu workstations to connect to terminal server running corporate wide applications.

Now the thing is, the workshop downstairs is geared up to rolling out a couple of hundred windows machines, and they have the whole images thing waxed.

What I am trying to do now is find out how to roll out as many ubuntu machines as possible, and the different methods that can be used for this.

What I have done is installed ubuntu, and updated all the updates, included things like the restricted extras and likewise-open (to connect to Active directory domains) and made sure the desktop was ready to be unpacked at the clients network and so that it would work right away.

A lost of these workstations will not have access to the internet at all, so I wont be able to install applications further down the line.

The guys downstairs tried to ghost the drive, but so far it seems that ghost and grub and the file system has issues so we need another option.

Is creating a tarball of the drive, copying it across to a new pc as per these instructions : [http://ubuntuforums.org/archive/index.php/t-525660.html](http://ubuntuforums.org/archive/index.php/t-525660.html) going to work?

Will I have to reinstall all the updates I have done.. like the likewise-open install? Will those instructions include everything I have installed?

All the workstations have the same hardware... but I just got to make sure its done right... so that when it gets on site and there is no internet connection... there are no problems.

Thanks for your time,
bushman

---

### Post by mxg01 on 2008-05-15
As for cloning the drive, have you tried Clonezilla? More info at [http://www.clonezilla.org/](http://www.clonezilla.org/) There is another 'clone a complete system to CD' program but I can't remember what it's called.

---

### Post by Partyboi2 on 2008-05-15
You could try [[COLOR=Blue]partimage[/COLOR]]("http://www.partimage.org/Main_Page") here is part of the description  from the website.
> **This utility can be used to install many identical computers**. For example, if you buy 50 PCs, with the same hardware, and you want to install the same linux systems on all 50 PCs, you will save a lot of time. Indeed, you just have to install on the first PC and create an image from it. For the 49 others, you can use the image file and Partition Image's restore function. 

---

### Post by w1z4rd on 2008-05-15
Thanks for the input chaps!

If I wanted to tarball an entire drive and all its files... so I could take that tarball to another drive, and extract it so I have a mirror of the first (this includes all packages I have installed and any edits I may have done to anything)... 

Whats the best set of commands to do that? I noticed the example only does a couple of directories, and I want to be sure I do not miss anything out.

Thanks!

---

### Post by mxg01 on 2008-05-16
I don't think that would work. Grub hangs off the master boot record and tar won't be able to access that. If you were to go down the tar route you'd need to copy the MBR using dd or an MBR utility. Then you'd have to install that MBR copy onto each machine and untar your archive. With the tar method you'd also have to create the file system (including swap space) on the target machine. 

With one of the imaging programs mentioned you wouldn't have to worry about creating the file system or the MBR. I'm not 100% sure about what happens with swap partitions on the target machines. Clonezilla does mention cloning a whole disk which I'd think would include the swap partition.

Personally I'd investigate Partimage and Clonezilla first. Clonezilla might be better as it's built on Partimage and includes extras. It also mentions cloning a whole disk. However, Partimage is in the repositories and Clonezilla is not.

---

### Post by w1z4rd on 2008-05-16
Hey,

Thanks for the response.

We will definitly be making use of the clonezilla and other clone applications for most of our work.. but I will have to train up staff to work with the software (They used to be MS techies in our company... so its going to take a while).

However, we have more than one network to roll out... I have another one that consists of only two work stations. Again, the hardware is the same on both. Instead of creating an image for this install, I thought a simply copy , zip and unzip would do okay.

What I did was setup the first machine as needed for the client. Then what I did with the second machine is install ubuntu (so it setups grub and the partitions and such. Now both of those computers will have the same hardware, and the same type of partitions. So worrying about copying partitions or messing with the MBR are not a problem. I just need to make sure I copy all the data from the one system, and be able to extract it to the other system. Hope this makes some sense...

Regards

---

### Post by mxg01 on 2008-05-16
In that case I think tar will work. 

So assuming you have a live CD and a USB hard drive, boot from the live CD, mount the USB drive and your source partition.

The run the tar command like this to create the archive on the USB drive:

tar -cf /mnt/usbdrive/image /mnt/sourcepartition/*

Option 'c' means create an archive and add to it. The 'f' means use the next bit as the archive. So 'image' will be your archive name. You can add a 'z' to the options (before the 'f' though) to pass the archive though gzip or a 'j' for bzip2. There is no point compressing the archive if your USB drive is big enough as it will slow things down.

Now boot the target machine from the live CD, mount the USB drive and the target partition. You must use the same mount point for the target partition as you used for the source partition as it's stored in the archive.

It would be worth taking a copy of /etc/fstab from the target machine as the disk/by-id values won't be the same and won't mount when you restart. Grub uses those disk by ID values too so take a copy of the /boot/grub/menu.lst file.

I'd also remove the existing directories from the target file system just to be sure you do end up with an exact copy. Then untar the archive like this:

tar -xf /mnt/usbdrive/image 

Now put back the menu.lst and fstab files, cross your fingers and reboot. 

It's quite a complicated process but I think it's only the disk/by-id files that won't be common. You could convert those files to the old format on the source machine. The /dev/disk values are generated during the boot process so it's no problem to copy /dev onto the new machine. I wonder how the clone programs handle those disk/by-id values. Anyway, report back as we may have missed something.

---

### Post by aquavitae on 2008-05-16
Have you thought of just using dd? I'd do it by booting off another drive (e.g. put the drive its installed on into another computer).

This will create an image of disk /dev/hdb in file ~/disk_image:
```
sudo dd if=/dev/hdb of=~/disk_image
```
Then save disk_image to a server/dvd/flash drive, go the the empty computer, boot of an ubuntu cd and do the following code:
```
sudo dd if=/path/to/disk_image of=/dev/hda
```
where /dev/hda is the blank drive in the new computer.
I'm not sure how this will work if you save disk_image onto the drive you're copying - you may end up with something recursive and a full drive.
I'm also not sure what will happen if the drives in the two computers are not identical.

Check man dd for the options.

---

### Post by mxg01 on 2008-05-16
Yes, dd would work. You can't do it to the same drive though. It crashes out with device full. I just tried it. If you did use dd you'd still have to sort out fstab and menu.lst manually.

---

### Post by aquavitae on 2008-05-16
Sorry, I forgot about fstab - I'm still used to the devices being specified by block device, in which case it wouldn't matter.  If its a straight forward setup you could change fstab in the original to use block device names, in which case that wouldn't be an issue. I wouldn't have though menu.lst would be a problem though as the devices are named there by disk order, e.g. (hd0,0).

---

### Post by tgalati4 on 2008-05-16
I did 10 machines in an hour using the simple copy command:

>sudo cp /dev/hda /dev/hdb

You need one master drive and a free IDE slot and simply swap drives in the second IDE slot.  Your copy drives need to be the same size (or larger) than the master.

No need to format or partition the copy drives.  Put the copy drives in a new chassis and boot.  I can't think of a simpler process.

---

### Post by aquavitae on 2008-05-16
Of course that would work! (same fstab provisions though)
I feel kinda stupid now you point it out!

---

### Post by mxg01 on 2008-05-16
It would be best to change to the good old method on the source fstab. I have seen Grub using disk/by-id in menu.lst, might not have been on Ubuntu though.

There are many ways to do this cloning. I suppose the clone programs would be best if you didn't want to start opening the boxes.

---

