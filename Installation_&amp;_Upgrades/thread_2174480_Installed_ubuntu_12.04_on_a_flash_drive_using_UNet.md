---
title: "Installed ubuntu 12.04 on a flash drive using UNetbootin now it says no disk space"
date: 2013-09-14
forum: Installation &amp; Upgrades
---

### Post by rv2 on 2013-09-14
I am new to Ubuntu  I installed ubuntu onto a flash drive that has 64gb of space on it.  It appears to install just fine.  A few minutes after I install it starts coming up with messages saying that I only have 153mb of space left.  When I look at the mount it knows that it is a 64gb drive.  I assume it has something to do with how it is mounting/partitioning the space, but I am not sure.  I was looking to install MySQL on there but I cannot because it thinks I have no space.  Any help would be very appreciated!

---

### Post by Quackers on 2013-09-14
Welcome to UF.
Did you partition the flash drive before you installed Ubuntu or was it previously partitioned?

Actually, when you say you installed ubuntu do you mean that you used Unetbootin to load the iso on to the flash drive?

---

### Post by rv2 on 2013-09-14
Thanks.
It had a single partition on it originally.  Unetbootin went through the whole installation, so I am not sure if it created a partition or not.

---

### Post by Quackers on 2013-09-14
I see - I think.
I suspect that you have downloaded an Ubuntu-xxxxxxxxx.iso file and then installed that file to your flash drive with Unetbootin.

If so, all that has happened is that the .iso file is now "burned" to the drive.
Now you need to boot your computer from that flash drive in order to install Ubuntu to your computer's hard drive - if that is your intention.
If that is not your intention please clarify.

---

### Post by rv2 on 2013-09-14
No, sorry, I'm not being clear.  I installed ubuntu on my flash drive with unetbootin.  The installation completed successfully and as part of the install it sets the flash drive to be bootable.  I restarted and selected to boot off of the USB.  That worked very nicely.  :-)   I can bring Ubuntu up and was able to connect to my wireless and get online, etc.  I started to download the MySQL binary, but now it comes up with a message that is warning me that I only have 153mb of space free.  In Windows I would go to explorer and look at how much disk space I have free on which partitions and could diagnose what is going on.  I'm not sure how to proceed in Ubuntu.  I can view all of my drives/mounts from within Ubuntu.  It appears from what it is showing me that I have a single partition on the USB drive that is 64gb in size.  When I reboot into Windows and look at the flash drive it indicates that I still have 53gb free.  So, I am not clear why the space does not appear to be available/visible to Ubuntu.  I am probably just being stupid, but it is not clear to me.

---

### Post by Quackers on 2013-09-14
Right, got you!
You are currently using Ubuntu live system. There is minimal free space for downloads in the live system regardless of the size of flash drive it's on. 
I am not familiar with MySQL so don't know what is downloaded and in what form.
What you could do is download it but save it elsewhere (not on the 64GB flash drive but on maybe another one).
Alternatively you could download it through Windows.

---

### Post by ajgreeny on 2013-09-14
OK, can you open a terminal with Ctrl+Alt+T and run command ```
sudo fdisk -l
``` and report the output back here.

I think what you have is a live system running from the USB, not a full install.
Is there an icon for "Install Ubuntu" showing anywhere? If so then you do just have a live system running, not an installed partitioned system.

---

### Post by rv2 on 2013-09-14
Yes, I could put it on another drive.  My intent is to have MySQL working on my flash drive.  I am trying to get a Linux development environment setup that runs off of the flash drive and is therefore portable and does not impact my physical drives at all.  I used a 64gb flash drive so that I would have lots of room to install things.  Unfortunately, in spite of having all of that space, I cannot use it.

---

### Post by rv2 on 2013-09-14
I do have an "install Ubuntu" icon showing on the desktop.  Let me boot back into ubuntu and run the fdisk

---

### Post by Quackers on 2013-09-14
You would be able to do what you want on that 64GB flash drive if you actually installed Ubuntu on to it rather than just loaded the .iso file.
You would then have about 60GB to play with.

If you have another 64GB flash drive, for instance, you could install Ubuntu from the live desktop you are now using to the second flash drive, then boot from that and you would have a full running Ubuntu install with loads of space left. You could then install whatever you want on it.

If you go that way make absolutely sure that you install grub to the second flash drive and NOT to your computer's hard drive. That would be BAD!!!
The option for installing grub is at the bottom of the partitioning section of the Ubuntu installation (selecting "something else" option rather than installing using the whole drive).

---

### Post by monkeybrain20122 on 2013-09-14
You need to install Ubuntu into the flash drive, you are running a live session if you created the bootable usb with unetbootin, Another thing is AFAIK unetbootin doesn't create live usb with persistence so every thing you install will be gone after a reboot,

To install Ubuntu on the usb, you need to have two usb drives (or a CD and a usb drive), one for installation, the other as the target to install Ubuntu into, This is like installing into your harddrive except that the target will be the flash drive.

So boot into a live session (with the live CD or a bootable usb drive created with unetbootin, since this is for installation only a 4 G usb drive is enough)
Now attach the target usb drive in the live session. In the terminal run "fdisk -l" and note the device name for the target usb drive (something like /dev/sdc, usually /dev/sda would be your internal drive, /dev/sdb would be your live usb) Then click install Ubuntu and  after the first few screen of time and location etc, you will be asked to choose the mode of installation, choose "something else"

When the installer shows you the partition table
1) choose the right device to install into (in this case /dev/sdc, say), if you are not careful you will install Ubuntu into the default internal drive and you will wipe everything there.
2) the drive has to be reformatted to ext4, and boot flag should be /
3) There is a box at the bottom of the install screen which asks you choose where to install the boot loader to, make sure you choose the target device (/dev/sdc), if you don't choose the default would be your internal drive, that way you won't be able to boot into the OS in your internal drive without the usb attached and your usb won't boot anywhere else except the computer with which it is created.

Then just wait.

Note 1: Ubuntu may be slow if you run it off a flash drive, you can get normal performance if you use an external hard drive instead.
Note 2: You can do more fancy partitioning like having a separate /home.

---

### Post by rv2 on 2013-09-15
Thanks for the reply.  I will give this a try today.  A few questions though, just for my uderstanding.  1) Will the new drive that I install Ubuntu on be a bootable drive, or will I always need to have both USB's to run everything?  2) Why wouldn't UNebootin just install a bootable full version of Ubuntu rather than the two step approach?  That seems odd.  3) I hear what you are saying about partitioning on a HD vs a flash drive.  But I would think that a flash drive would be faster since it is purely electronic/digital while the HD has a mechanical component to reads/writes.  That seems counterintuitive to me.

Thanks again, I really appreciate the help.

---

### Post by Quackers on 2013-09-15
The new installation will be bootable when it is plugged in to your computer at boot. Again - make sure grub is installed to your flash drive and NOT your computer's drive. This is very important! Your computer won't boot if you make that mistake!

Unetbootin only installs the Ubuntu.iso file. That's all it's designed to do. Your computer and that Unetbootin-installed iso file do the installing.

Yes, it is odd, but I can confirm that Ubuntu running on a flash drive is not very fast. I don't know why that is. It is not what I expected in that respect. But it does work!

---

### Post by ajgreeny on 2013-09-16
> **Quackers said:**
> Yes, it is odd, but I can confirm that Ubuntu running on a flash drive is not very fast. I don't know why that is. It is not what I expected in that respect. But it does work!

That is presumably because the of  usb2 transfer speed of any data is very much slower than that of a standard installation on a normal spinning disk sata drive.

I wonder what it would be like on a usb3 port and drive, if it's possible to boot from them.

---

### Post by oldfred on 2013-09-16
Even on a USB2 port my new USB3 flash drive is about 10% faster.

I find install on flash drive acceptable, just not speedy. Install is slow as writing is always slow. But you can turn off some write activity which helps. Once application is loaded into RAM it is cached and reuse then is very quick. Or more RAM helps.

If using system with multiple PC, do not install proprietary video or other drivers as that may create conflicts. Or plan work arounds to boot with correct video.

 With SSD or Flash (trim do not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
      
 After installing, change the fstab so that everything gets mounted with noatime.


I installed full Ubuntu in 8GB of my 16GB flash drive with the other 8GB for data. But I do not install a lot of software. I use it more as an emergency boot drive and another install/repair drive booting ISO directly from grub.

---

