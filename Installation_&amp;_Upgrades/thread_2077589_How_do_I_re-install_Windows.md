---
title: "How do I re-install Windows"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by Airycat on 2012-10-28
I have several programs I need to use and they do not have Linux versions and there is nothing more I can try to get them to work on Ubuntu. I decided I had to re-install windows, but when I tried, it said it couldn't because the hard drive (2 partitions) is not the right format. What do I need to do to be able to install windows again?

---

### Post by oldfred on 2012-10-29
Windows has to have a primary (sda1 thru sda4)  NTFS formated partition with the boot flag. Or unallocated space so it can create a primary NTFS partition.

Windows 7 will usually want 2 partitions the first is a small 100MB boot/repair partition. But if you have a preformatted partition it will totally install to that partition. 

Either way you should then immediately make the Windows repairCD or USB so you have a way to repair Windows if you have issues.

---

### Post by uRock on 2012-10-29
You can use an ubuntu install disk to repartition the hard drive. Once the ubuntu live image is booted, search for GParted or Partition Editor. Back up your data first!

---

### Post by Mark Phelps on 2012-10-29
> **Airycat said:**
> I have several programs I need to use and they do not have Linux versions and there is nothing more I can try to get them to work on Ubuntu. I decided I had to re-install windows, but when I tried, it said it couldn't because the hard drive (2 partitions) is not the right format. What do I need to do to be able to install windows again?

Are you trying to do a clean reinstall from Windows CD/DVD? Or, are you trying to do a restore from a Recovery partition?

Asking because the clean reinstall should give the the option to reformat the drive -- in which case, it won't care about the format of the existing partitions.

---

### Post by Airycat on 2012-10-29
> **Mark Phelps said:**
> Are you trying to do a clean reinstall from Windows CD/DVD? Or, are you trying to do a restore from a Recovery partition?

Asking because the clean reinstall should give the the option to reformat the drive -- in which case, it won't care about the format of the existing partitions.

There is a reason I'm asking about this in the Absolute Beginners Section.

I want to do a clean install. I want to put Windows 7 back and install Ubuntu as WUBI because I have about 4 programs that will not work with Linux and I've been trying everything for the last 9 months. 

I put the disk in and selected the CD/DVD drive and it uploaded files and then I got the problem with not being formatted correctly. Now I don't even have the CD/DVD drive option. (It's disabled for some reason I don't know.) I don't remember an option to reformat, but that's not saying it wasn't there.

So a really basic question:  **How do I get the computer to run the CD for a clean install?**

---

### Post by oldfred on 2012-10-29
Try a full power down or cold boot. If a laptop remove battery for a bit.

Then go into BIOS or use one time boot key to choose CD/DVD to boot.

---

### Post by TheMTtakeover on 2012-10-30
> **Airycat said:**
> There is a reason I'm asking about this in the Absolute Beginners Section.

I want to do a clean install. I want to put Windows 7 back and install Ubuntu as WUBI because I have about 4 programs that will not work with Linux and I've been trying everything for the last 9 months. 

I put the disk in and selected the CD/DVD drive and it uploaded files and then I got the problem with not being formatted correctly. Now I don't even have the CD/DVD drive option. (It's disabled for some reason I don't know.) I don't remember an option to reformat, but that's not saying it wasn't there.

So a really basic question:  **How do I get the computer to run the CD for a clean install?**

You can do a dual-boot so you can have both but would save you from using wubi.
To answer your really basic question go into your BIOS and change the boot the order.

---

### Post by Mark Phelps on 2012-10-30
> **Airycat said:**
> ... 
I put the disk in and selected the CD/DVD drive and it uploaded files and then I got the problem with not being formatted correctly. ..

My suspicion is that this is NOT a Windows setup disk, but instead, a Windows Recovery disk.

If the version of Windows is 7, and this is really a CD, not a DVD, then my suspicion is correct -- and you are out of luck -- because you can't reinstall Windows using that disk if you have messed with the partitions on your PC -- which it sounds like you have.

You will need a Windows SETUP DVD -- and it is a DVD, not a CD.  When you launch that, it should give you the option of erasing the partitions currently on the drive.

If even that doesn't work, then boot your PC from an Ubuntu LiveCD or LiveUSB and use the GParted app to remove all the partitions on the drive.  Then, reboot with the Windows Setup DVD.

---

### Post by Airycat on 2012-10-30
**1.)**  After a lot of clicking, I finally was able to get to a place where I had the option to format, but I didn't really have it. It's nonfunctional. 

[[img]http://farm9.staticflickr.com/8184/8139543750_2b457b780f.jpg[/img]](http://www.flickr.com/photos/airycat/8139543750/)
[DSC07775a](http://www.flickr.com/photos/airycat/8139543750/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

I suspect that the only way to get Windows back is to delete, but I didn't want to do that without verifying  that it's the right thing to do.

> **Mark Phelps said:**
>  it should give you the option of erasing the partitions currently on the drive.

Is this a yes answer? Is an "Ubuntu LiveCD" running Ubuntu from the CD rather than from be hard drive? (I am using the reinstallation DVD.)

**2.)**  How do I dual boot? I thought wubi was the only way to have both, but I would not mind not turning on Windows if I don't need those Windows specific programs.

---

### Post by squakie on 2012-10-30
If you have a fairly modern system (post the specs back and we can see), if you have only 4 programs you need Windows for, why not leave ubuntu on the system and use something like VirtualBox to run Windows in a virtual machine with linux.  That way your Windows programs are always available and you still get to run linux.

As Mark has mentioned, the biggest thing is if you have a recovery CD or an installation CD as you'd need the installation CD to install Windows in the virtual machine.

I run both Windows XP and Windows 7 in virtual machines in Ubuntu, but also have dual-boot for Windows 7 as well.

my specs:  8-core AMD @ 3.1ghz, 16gb memory, 1.5tb sata hard drive, 60gb sata ssd, nVidia GeForce GS 450, the usual things like wireless, card reader, DVD-DL R/W, etc..  I'm lucky in that I can dedicate more than 1 cpu to each virtual machine as well as memory and still have plenty left for ubuntu to run also.

---

### Post by uRock on 2012-10-30
You'd have to delete the partition, then create a new one.

Here's a great for learning to dual boot,
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Personally, I'd recommend installing ubuntu into a virtual machine, so that you can boot into ubuntu without having to restart. That is what I have to do because of hardware issues.

---

### Post by Airycat on 2012-10-30
> **squakie said:**
> If you have a fairly modern system (post the specs back and we can see),

Memory: 5.8 GiB
Processor: Pentium Dual-Core CPU E5400 @ 2.7 GHz x2
Graphics: Unknown *
OS Type 64-bit
Disk: 623.8 GB

*I don't understand why the Graphics is unknown. When I bought the computer, I specified that I need one that would work with graphics intense programs and more than one at a time. (One of these, my machine embroidery designer, is one of the programs that doesn't work in Linux and requires a dongle[usb] to use.)

> **squakie said:**
>  if you have only 4 programs you need Windows for, why not leave ubuntu on the system and use something like VirtualBox to run Windows in a virtual machine with linux.  That way your Windows programs are always available and you still get to run linux.
...
I run both Windows XP and Windows 7 in virtual machines in Ubuntu, but also have dual-boot for Windows 7 as well.

This is what I really *want* to do!! I have been trying to make this (or wine) work since I installed Ubuntu in January, with no success. I have another thread on trying to get Win 7 to work in VirtualBox. You (squakie) responded there, but I'm lost already because it won't install the Win7 (it says I'm trying to load 64 on 32). Obviously, I'm doing something wrong, or I simply don't have the capacity. 

Does the info I gave above tell you if I have the capacity? If not, where do I find what you need to know? If I have the capacity to install Windows 7 in a virtual box, can you give me clear step by step instructions from installing VirtualBox to a functional Win 7?  

And also, all I had was a tiny window and that won't work for me. I already have to magnify to 150% to be able to read websites on my 17" screen. To use that embroidery program, I must be able to see detail.

I deleted the VirtualBox I had since it wasn't letting me install my 64 bit Win7. Afterward, I got to thinking that perhaps it was set up incorrectly. I remember my brother (who put it in for me) asking me about whether I needed 64 or 32. I know I *told* him my Win7 was 64, but I don't know what he did. Maybe he made the VirtualBox a 32 in error. ?? I'm not usually so dense about computer stuff and I can figure things out, but I'm also not really a computer geek.

---

### Post by squakie on 2012-10-31
You may want to check the version of Ubuntu you downloaded and installed.  By default you will get the 32-bit version - you have to select 64-bit get 64-bit OS.  Oracle's VirtualBox download is also split - 32-bit or 64-bit (it's further down the page from the 1st list of linux downloads).  Obviously you'll need a 64-bit ubuntu install to install the 64-bit VirtualBox.  It sounds like your Windows is 64-bit and your VirtualBox is 32-bit.  Make sure they all match - 64-bit ubuntu, 64-bit virtualbox, 64-bit Windows 7.  You will need to completely reinstall ubuntu if you need to install the 64-bit version.  Similarly, I would delete the existing VirtualBox before installing the 64-bit version.

Hope that makes sense - I can't always say things the way I see them in my head......

edit: my friends have 2 Singer SX or XS or something 6000's that are embroidery/sewing machines.  They've had problems getting at least one of their softwares (I don't know which) even run on Windows 7, so I understand the need.  You can have the VM just start when the system boots so you'll always have the ability to switch to a Windows window on the fly.  If you don't need your Windows running all the time, it would be best to only start VM when you need it, and then shut it down when you don't need it anymore.  It will release the resources back for your ubuntu to use.

---

### Post by Mark Phelps on 2012-10-31
> **Airycat said:**
> **1.)**  After a lot of clicking, I finally was able to get to a place where I had the option to format, but I didn't really have it. It's nonfunctional.

From the screenshot, there is no Free Space.  The solution is to pick the partition and then click the Format icon at the bottom of the screen.  It doesn't look "grayed out" -- so it looks like it would work.

Are you saying that when you click the Format icon, installation won't continue?

---

### Post by Airycat on 2012-10-31
> **Mark Phelps said:**
> From the screenshot, there is no Free Space.  The solution is to pick the partition and then click the Format icon at the bottom of the screen.  It doesn't look "grayed out" -- so it looks like it would work.

Are you saying that when you click the Format icon, installation won't continue?

There's no free space because it's in Ubuntu format and yes the format button actually is grayed out.

---

### Post by Airycat on 2012-10-31
> **squakie said:**
> You may want to check the version of Ubuntu you downloaded and installed.  

I was certain I had the 64 bit installed and that's what it says in System Settings Details, but all I'm finding is a 32 bit disk. The version I currently have is from the updates, and frankly, it's been a lot of trouble since I updated. So, since I already have everything backed up. I'm going to dl the 64 bit to disk and re-install it. I'm hoping a clean install will clear things up all around.


> **squakie said:**
> edit: my friends have 2 Singer SX or XS or something 6000's that are embroidery/sewing machines.  They've had problems getting at least one of their softwares (I don't know which) even run on Windows 7, so I understand the need.  You can have the VM just start when the system boots so you'll always have the ability to switch to a Windows window on the fly.  If you don't need your Windows running all the time, it would be best to only start VM when you need it, and then shut it down when you don't need it anymore.  It will release the resources back for your ubuntu to use. My software had a lot of problems with Win7 until they (software co.) came up with some fixes. It worked fine before I got Ubuntu. It works ok on my laptop xp, except the laptop is  soooooooooooooo slooooooooow.

---

### Post by Mark Phelps on 2012-11-01
> **Airycat said:**
> There's no free space because it's in Ubuntu format and yes the format button actually is grayed out.

The format has nothing to do with the lack of space. To install Windows you need UNALLOCATED space.  Free space inside an existing partition will do you no good.

OK, if the format button is grayed out (even though it does not look like that on the screen), then use an Ubuntu LiveCD or Live USB, boot to a desktop, and run GParted (Gnome Partition Editor) -- and REMOVE the existing Linux partitions.

After that, you should be able to reinstall Windows.

---

### Post by cmcanulty on 2012-11-01
look in your bios I had to enable virtual 64 there then win 64 bit installed in virtual box

---

### Post by Airycat on 2012-11-04
I have tried and tried to install Win7. I keep getting the same message (#9). 

Next I tried to install VirtualBox again. I had to reinstall Ubuntu to make sure I had the 64 bit, since my DVD says 32-bit (which I use for my Mom's computer) and I couldn't find another. No problems there, but somehow my password was destroyed and now I can't do anything in a terminal. So I tried to reinstall it. HA!! Doesn't work, it merely boots what I have. 

Evidently it was a dumb idea, but I thought, if I install the 32-bit version (which it would/did do), then I van put in the 64-bit version to reinstall, but it still just boots up what I already have--the 32-bit OS. So now, I'm stuck with the OS I totally don't want and I have no idea how to get back.

What am I missing to install the OS I want? What do I need to do to get it to install? I know the dvd is OK because it installed before (when I messed up my password).

How do I simply wipe my computer clean so I can put on the OS I want (either Ubuntu 12.10 64-bit with a functioning Windows 7 Virtualbox, or Windows 7)?

All I want is a computer that works, one in which I can run the programs I need. One that doesn't need me to constantly be doing computer geek stuff for which I'm not at all qualified.

---

### Post by oldfred on 2012-11-04
Did you use manual install and tell it to use the same partitions. Any of the auto installs just shrink what you have and try to add a new / partition. And if that did not install grub correctly you end up booting the old install.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by Bucky Ball on 2012-11-05
*Thread moved to **Installation & Upgrades***

---

### Post by Airycat on 2012-11-05
> **oldfred said:**
> Did you use manual install and tell it to use the same partitions. Any of the auto installs just shrink what you have and try to add a new / partition. And if that did not install grub correctly you end up booting the old install.

A reason I originally had this in absolute beginners forum.... I don't know how to install other than to insert the disk into the drive. I put the DVD in the drive and click F12. Sometimes it works. Sometimes it doesn't. 



> **oldfred said:**
> 
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

I got these messages 
for the Full RepairCD with Boot-Repair
[[img]http://farm8.staticflickr.com/7108/8156888034_ebf0115a87.jpg[/img]](http://www.flickr.com/photos/airycat/8156888034/)
[Screenshot from 2012-11-04 22:12:38](http://www.flickr.com/photos/airycat/8156888034/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

Ooookay... seems it took forever to download, and the usual box I get saying something is downloading did not show up, so I thought it was done. I just got a notice for it. Guess that explains the extra files. (?)  Fixed that  & I'll try it again.

for the Boot Repair:
[[img]http://farm9.staticflickr.com/8490/8156900502_2b469b520f.jpg[/img]](http://www.flickr.com/photos/airycat/8156900502/)
[Screenshot from 2012-11-04 22:26:10](http://www.flickr.com/photos/airycat/8156900502/) by [Airycat](http://www.flickr.com/people/airycat/), on Flickr

Since this latter one seems to have done something, I'm going to try again. If it doesn't work, I'll be back asking for help about manual installation

---

### Post by oldfred on 2012-11-05
Easier for everyone if you had posted the link, not a screenshot of the link.

[http://paste.ubuntu.com/1334098/](http://paste.ubuntu.com/1334098/)

You should be able to use gparted from the liveCD to shrink the Linux partition sda1. Then create a NTFS partition sda2 and move boot flag to that partition.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Resizing an Ubuntu System Partition Use liveCD so everything is unmounted & swapoff if neccesary
[http://ubuntuforums.org/showthread.php?t=1219270](http://ubuntuforums.org/showthread.php?t=1219270)

---

### Post by Airycat on 2012-11-05
OK here's the thing. I have a 32 bit Ubuntu installed and I need the 64 bit. 

I'd rather have Ubuntu and have either a dual boot with Windows or a Virtualbox, but I have to have the right version first. I have the correct version on disk. I know it's good because I've used it before. 

:?:   What do I do to make the dvd overwrite the version on my computer? (Either Ubuntu or Windows, at this point.) After I get the right version on the computer, then I'll look closer at the dual boot tutorial.

I apologize about the screenshot vs, link. I was not thinking and I hadn't looked at  it myself, yet, which is just as well because I don't understand it.

:popcorn:  Have some popcorn. I'd give you all cookies for helping, if they were in the smilies (or real ones if you were actually here).  Thank you!

---

### Post by oldfred on 2012-11-05
If you have anything to backup do that first.

Best to also have Windows repairCD or USB if you do not have that.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Then in the Ubuntu installer CD or USB choose to use Something else or manual install. Be sure you know which partition is your Ubuntu install. From liveCD use fdisk to list partitions if not sure.
From Something else it will ask you all the typical questions keyboard, language, location, etc,  but also show the partitions. You choose your existing 32bit install partition, reformat to ext4 and use as / (root). If your current swap is ok, it will find it and reuse it automatically. If you have an existing /home choose it but do not choose to reformat. If you have more than one drive choose where to install the grub2 boot loader, but do not choose partitions.

---

### Post by Airycat on 2012-11-06
Is it just weird or did I really have to burn a new dvd to get the os to install? That was the only thing that worked, but it did work.

Anyway, I have the current 64 bit Ubuntu and I'm going to end this thread and move on to trying to get VirtualBox to work. If problems with that persist, I'll look into those dual boot links.

Thank you to everyone who responded to this problem.

---

