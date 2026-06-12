---
title: "Multiple Boot system"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by rodst on 2009-12-30
I want to trial Ubuntu but have hundreds of questions about the ability to run existing programs/facilities (e.g. Dreamweaver, CCTV software, 3G dongle ADSL access etc. etc.). 
 
However, before investigating these questions, in the first instance I want to install Ubuntu 9.10. I have two HDDs; the primary HDD has 2 partitions with XP on one and data on the other. The secondary HDD has a backup copy of XP on the first partition and two other partitions (one for backup data and the other CCTV footage). My plan is to install Ubuntu on the 2nd HDD overwriting the backup copy of XP.
 
To do this, I intend to change the boot sequence in the BIOS to boot from CD, then secondary HDD. This will ensure that Ubuntu will load from the CD and I can install it on my secondary HDD.
 
However, I am concerned that Ubuntu may find the copy of XP on my primary HDD (that will, of course, now temporarily be my secondary HDD after I change the BIOS boot sequence) and "corrupt" it. I could of course disconnect my primary HDD to protect it (which is the way I built the multiple boot system for XP) but this is just a little painful as I have to physically move a lot of furniture!!
 
Can anyone please advise me of the risks of installing Ubuntu on a second HDD whilst Windows resides on the other HDD?
 
I am assuming also that there is something equivalent to boot.ini in Ubuntu so that I can select at boot time which OS I can load.

---

### Post by Herman on 2009-12-30
Well I've been installing Ubuntu with Windows for years now, almost since Ubuntu first came out. I've installed every Ubuntu that ever came out many times for making my website for telling other people hwo to do it and I install Ubuntu for friends who live in my area. I have never had the Ubuntu installer do anything I didn't tell it to do.

 ... well *once*, but that was due to a hardware problem - a dusty lens in an optical drive, it cause a corrupted partition table. I was able to fix that with TestDisk.

You are advised to make a backup of your important files as per normal when working with disc partitioning software.

The chances of anything going wrong are fairly remote though, I never bother unplugging other hard disks. Ubuntu doesn't have the same bad habits Windows has. :)

Just make sure you know how to tell which hard drive of yours is which and make sure you read properly and think carefully before make each decision since it will be your first time.
 
By default, Ubuntu will install the IPL for the GRand Unified Bootloader in the boot code are of the MBR of the first hard disk. In your case, that will be the same hard disk as you're installing Ubuntu in.

That will be okay as long as you're going to leave your hard disks numbered that way. It will add an entry for Windows XP as a second hard disk installation, which will mean it will include a couple of map commands, and everything will be fine.

If, however, you're thinking of reverting your hard drives back the other way around later on at some stage after the install, you'll only have the Windows loader in number 1 hard disk, which will only boot Windows.
That will be okay, but when you want to boot Ubuntu then, you'll be putting yourself through the un-necessary inconvenience of having to boot through your BIOS.
Therefore, you might be better off leaving your hard disks set in the order you want them to be in later. That way the GRand Unified Boot loader will be set up correctly for booting both operating systems. The MBR is not part of the Windows partition. The Windows boot sector is. It's safe to install GRUB to MBR in any hard disk and it won't corrupt your Windows installation, but don't ever install GRUB to the Windows boot sector, (first sector of the Windows partition).

Usually, the people who just relax and install Ubuntu have no trouble, but the people who are apprehensive and take extra precautionary measures like switching hard disks around or unplugging them, are the ones who make things confusing for themselves (and everyone else later when they need help).

---

### Post by rodst on 2009-12-30
Thanks Herman for the info; it's much appreciated...... and for the hyper links. Will "set to" and plan the work.

---

### Post by rodst on 2009-12-30
A question please Herman now that I have started on the planning phase.
 
My two HDDs are as follows:
 
Primary HDD has C:\ containing XP and D:\ containing data.
Secondary HDD has G:\ containing 2nd copy XP, H:\ containing backup of data and J:\ containing CCTV footage.
 
On my primary HDD in C:\ is the following boot.ini file:
 
> 
[SIZE=1][boot loader][/SIZE]
[SIZE=1]timeout=10[/SIZE]
[SIZE=1]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/SIZE]
[SIZE=1][operating systems][/SIZE]
[SIZE=1]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Main_Win XP " /Fastdetect /NoExecute=OptIn[/SIZE]
[SIZE=1]multi(0)disk(0)rdisk(1)partition(1)\WINDOWS="Alternative XP on secondary for tests" /Fastdetect[/SIZE]

 
When I start to install, the question is, after changing my BIOS to boot from the secondary HDD (though I will boot Ubuntu from the CD), do I simply leave the 3 partitions on the secondary HDD and install Ubuntu (in effectively the G:\ partition) overwriting the 2nd copy of XP
 
Or do I install Ubunto on the whole of the 2nd HDD erasing all the data (G:\, H:\ and J:\) all of which I can afford to lose and allow Ubunto to partition the 2nd HDD into 3 partitions?
 
If I opt for the latter, will XP still recognise the partitions created by Ubuntu?
 
If I switch the BIOS back to boot from the primary won't it still give me the option to select the boot from "Alternative XP on secondary" (even though it is not XP that will be booted)?
 
If I leave the BIOS to boot from the 2nd HDD, is it possible to change the boot loader in Ubuntu on the 2nd HDD after installing Ubuntu so that I have the option to load XP from the primary HDD?

---

### Post by Herman on 2009-12-30
:) What does 'C:\' drive mean, and what does 'G:\' drive mean?
Okay, I know, your 'A:\' drive is your floppy disk drive and your 'B:\' drive is your big floppy disk drive that nobody had anymore. Actually, not too many people use floppy disks at all much nowadays. 
Okay, so your 'C:/' drive is your Windows drive, your 'D:/' drive is your CDROM drive, and other drives after that will be assigned more letters from the alphabet.

In Linux we have a completely different way of naming and numbering our hard disks and partitions.
"Linux Device Numbering"
Hard drive 1 is called /dev/sda
Hard drive 2 is called /dev/sdb
Hard drive 3 is called /dev/sdc ... and so on if there are more hard disks or even USB drives plugged in to the computer.

Hard drive 1, partition 1 is called /dev/sda1
Hard drive 1, partition 2 is called /dev/sda2 ... and so on ...

In my opinion, it's a much better system of numbering, because from the device number we can tell what drive number it is and partition number it is that we're talking about exactly, while the letters of the alphabet tell us almost nothing. :)

---

### Post by yelvington on 2009-12-30
You're making this harder than it needs to be.

Don't remap your drives, mess with your BIOS, etc. The only reason to touch the BIOS would be to get your computer to boot from the CD, if it doesn't already do so.  With many systems even that can be done without touching the BIOS.

Boot from the Ubuntu installation CD into a live session (NOT the installer). 

Before you install, make ABSOLUTELY certain that Ubuntu likes your hardware. Run the system for awhile from the CD. It'll be slow when loading programs, but it should work just fine. Only after you're satisfied that your hardware and Ubuntu will get along should you run the installer.

Then run the installer from the menu entry. Walk through the first couple of screens (select your language, your keyboard layout, your timezone, etc.), and when you get to the disk partioner, STOP and look very carefully about what you're going to do.

On the first page of the disk partioner, switch to MANUAL mode.  You now will be presented with a colorful graphical display of each existing disk partition, showing the operating system and filesystem types.

Your first physical disk will be /dev/sda, and you do not want to use that one. Figure out which of the remaining physical disks is your secondary HD -- /dev/sdb, /dev/sdc, etc. It should be quite obvious, as Ubuntu will identify what it found on each of the drives.

You can repartition/reformat the entire drive OR existing partions as you wish, preserving any parts you want to preserve. 

You will at least need to specify a partition for Ubuntu to be mounted at '/' formatted as ext4, and a swap partition. 

When you're done, the installer will apply the changes, unpack the software, and write a new bootloader in the boot sector of your PRIMARY hard disk. 

This new bootloader will include options for all the operating systems that Ubuntu has found, so you will have no trouble booting into Windows.

---

### Post by Herman on 2009-12-30
It's up to you if you want to switch your drive order around in the BIOS or not, it won't matter much but by switching them around and then switching them back again you're just making more work for yourself.

---

### Post by oldfred on 2009-12-30
I always like to have each operating system on separate drives and that drive have its MBR boot to that operating system. Since grub/ubuntu is more flexible and can easily boot windows from the second drive I always make Ubuntu first. If there is ever a problem with the first drive I can still boot the second. When the boot loader is on one drive and the system on another both drives have to be working for the entire system to boot.

Also there is a minor bug in grub2 currently. It has a ~20 sec delay if grub is in one drive and Ubuntu is on the other drive. When I switch sdc to be the boot drive grub comes up almost instantly whereas before it was very slow.

---

### Post by rodst on 2009-12-31
Thanks everyone for the help. Have a version of Ubuntu loaded and able to boot into XP and Ubuntu. Not perfect but okay to evaluate. I have my first question now but wil lstart a new thread. Thanks again.

---

