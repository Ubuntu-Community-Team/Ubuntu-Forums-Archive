---
title: "Trying to install Ubuntu* over Vista"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by OutCell on 2008-04-10
Hi,

I have an old Dell Dimension 8300 desktop that i installed Vista on last year. Yesterday i tried to install Ubuntu Server 7.10 over Vista Ultimate which i didn't want anymore and couldn't do so because the partitioning froze at 33% during the install. Then i tried Ubuntu 7.04 Desktop and the live CD worked ok but when i try to install it froze at 3%.

When i tried to reboot the desktop and try again i get this screen:
BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) _


Then i tried Ubuntu 8.04 beta and i get the same screen when trying the Live CD or install!

Is there a certain way i should install Ubuntu on Vista because of vista's partition?
I would appreciate your input and help as soon as possible because my desktop is not working at the moment :P

---

### Post by warp99 on 2008-04-10
You need to install the OS with some boot options:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

I would try the kernel options 'noacpi' and 'irqpoll' to see if that works better. Also if this is a server install then you should use the 'Alternative CD' instead of the GUI install. Go to the ubuntu.com download page and tick the box marked 'Check here if you need the alternate desktop CD.' 

You understand that Ubuntu Server does not install a desktop for security purposes, correct?

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> You need to install the OS with some boot options:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

I would try the kernel options 'noacpi' and 'irqpoll' to see if that works better. Also if this is a server install then you should use the 'Alternative CD' instead of the GUI install. Go to the ubuntu.com download page and tick the box marked 'Check here if you need the alternate desktop CD.' 

You understand that Ubuntu Server does not install a desktop for security purposes, correct?

Thanks for the quick response :)

Well in the beginning i tried the ubuntu server alternative cd (7.10) but when that didn't work i just wanted to install any ubuntu desktop. I am trying to make this box a media server and after reading some articles i decided to just install ubuntu desktop for a GUI and then install BlackBox manager for less memory use instead of gnome. (Read this in Linux Format magazine, May 08)

I installed ubuntu several times on laptops before but none were Vista based, they were XP; so i thought Vista might need some special requirements to delete ..

---

### Post by warp99 on 2008-04-10
Vista doesn't need anything special. Try the 'noacpi' and 'irqpoll' options when you install and still use the 7.10 alternate CD since you can install a regular ubuntu desktop with that CD. If your looking for a media server and have a TV tuner card you can try Mythbuntu:

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

This will give you a full blown PVR media server, basically a Tivo with a lot of extra goodies. Just make sure your TV tuner card is compatible before installing.

---

### Post by jimbo99 on 2008-04-10
I don't understand what you mean over Vista.  You mean as a dual boot?  Or are you wiping the partition to start fresh from scratch?

What are the reasons you are moving from Vista (other than it sucks badly)?  Are you switching because of odd behavior of the OS (not counting bad software design)?

I have installed Ubuntu on a lot of computers, an awful lot.  I have encountered quite a few errors.  Some things to keep in mind:

1) Burn the live CD at a low rate (such as 4x or 1x).
2) Run the memory test from the CD if you can get it to boot and run it for a long time, such as over night.  Any error it finds indicates that you have a memory error and you should try to identify which stick itis.
3) Often the CD/DVD drive you are using can be the cause of failed installs.  I found that through experimentation when I accessed the installer with one DVD/CD drive it would fail to install only doing so partially, and other times wouldn't install at all until I temporarily replaced the drive with a different one..often an older drive worked whereas the newer models failed.
4) The HDD may have a fault and  you should test it with the manufacturers diagnostic tools. Those can generally be found at the manufacturer's web site.  If it finds bad sectors try to low level the drive before you do the install.

If you are trying to do this as a dual boot, well, you have the added problems of dealing with the boot loader configurations and with two operating systems (partitioning the drive, copying profile info, etc).  If you are trying to do this with Wubi then you have the complexities that go with it.  If you are, then I'd suggest that when you finally begin to have some success you give the Ubuntu virtual drive max space.  Don't try to install it in the minimal configuration because as time goes by you'll end up running out of room for program updates, new programs, etc.

I have machines running in each configuration (wubi installs, dual boot vista, dual boot XP, and dedicated Ubuntu).  It's possible to have great results with all sorts of configurations but the more complex the configuration the more knowledge you need to have.

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> Vista doesn't need anything special. Try the 'noacpi' and 'irqpoll' options when you install and still use the 7.10 alternate CD since you can install a regular ubuntu desktop with that CD. If your looking for a media server and have a TV tuner card you can try Mythbuntu:

[http://www.mythbuntu.org/](http://www.mythbuntu.org/)

This will give you a full blown PVR media server, basically a Tivo with a lot of extra goodies. Just make sure your TV tuner card is compatible before installing.

Thanks again

I don't have a TV tuner, i just want to stream media through the network..

Can you please tell me more about noacpi and irqpoll? i don't know what these are..

---

### Post by OutCell on 2008-04-10
> **jimbo99 said:**
> I don't understand what you mean over Vista.  You mean as a dual boot?  Or are you wiping the partition to start fresh from scratch?

What are the reasons you are moving from Vista (other than it sucks badly)?  Are you switching because of odd behavior of the OS (not counting bad software design)?

I have installed Ubuntu on a lot of computers, an awful lot.  I have encountered quite a few errors.  Some things to keep in mind:

1) Burn the live CD at a low rate (such as 4x or 1x).
2) Run the memory test from the CD if you can get it to boot and run it for a long time, such as over night.  Any error it finds indicates that you have a memory error and you should try to identify which stick itis.
3) Often the CD/DVD drive you are using can be the cause of failed installs.  I found that through experimentation when I accessed the installer with one DVD/CD drive it would fail to install only doing so partially, and other times wouldn't install at all until I temporarily replaced the drive with a different one..often an older drive worked whereas the newer models failed.
4) The HDD may have a fault and  you should test it with the manufacturers diagnostic tools. Those can generally be found at the manufacturer's web site.  If it finds bad sectors try to low level the drive before you do the install.

If you are trying to do this as a dual boot, well, you have the added problems of dealing with the boot loader configurations and with two operating systems (partitioning the drive, copying profile info, etc).  If you are trying to do this with Wubi then you have the complexities that go with it.  If you are, then I'd suggest that when you finally begin to have some success you give the Ubuntu virtual drive max space.  Don't try to install it in the minimal configuration because as time goes by you'll end up running out of room for program updates, new programs, etc.

I have machines running in each configuration (wubi installs, dual boot vista, dual boot XP, and dedicated Ubuntu).  It's possible to have great results with all sorts of configurations but the more complex the configuration the more knowledge you need to have.

I appreciate your reply.

I meant replacing vista with ubuntu because i want to make that desktop a media server. I already have vista on my laptop and using it daily but as soon as i finish university i will replace it with ubuntu. For now i need some special 3D programs that work on windows..

My CD is good, the live cd worked but then i got that msg!

---

### Post by warp99 on 2008-04-10
> **OutCell said:**
> Thanks again

I don't have a TV tuner, i just want to stream media through the network..

Can you please tell me more about noacpi and irqpoll? i don't know what these are..

I posted the link earlier in the thread, but you must have missed it. So here it is:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

Both noacpi and irqpoll are boot options that can be appended to a kernel string when the hardware is not behaving, such as in your situation. The boot options link has some graphics and step by step instructions on how to append the kernel string. It also gives a brief description on what the boot options do.

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> I posted the link earlier in the thread, but you must have missed it. So here it is:

[https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29](https://help.ubuntu.com/community/BootOptions?highlight=%28bootoptions%29)

Both noacpi and irqpoll are boot options that can be appended to a kernel string when the hardware is not behaving, such as in your situation. The boot options link has some graphics and step by step instructions on how to append the kernel string. It also gives a brief description on what the boot options do.

Thanks

So i just press F6 and then type:
pci=noacpi irqpoll

in the end of that line?

It is not very clear for me as i am not that good with linux

---

### Post by warp99 on 2008-04-10
> **OutCell said:**
> Thanks

So i just press F6 and then type:
pci=noacpi irqpoll

in the end of that line?

It is not very clear for me as i am not that good with linux

I would use 'noacpi' or 'acpi=off' and 'irqpoll' since pci=noacpi is just for the pci bus, but yes it's F6 and the parameters. Now once you have the OS installed you may have to add one of those parameters to you're boot string permanently, but we'll cross that bridge later if we need to.

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> I would use 'noacpi' or 'acpi=off' and 'irqpoll' since pci=noacpi is just for the pci bus, but yes it's F6 and the parameters. Now once you have the OS installed you may have to add one of those parameters to you're boot string permanently, but we'll cross that bridge later if we need to.

Thanks. acpi=off irqpoll worked! I'm in the live CD now.. Should i just install again like i did before?

---

### Post by warp99 on 2008-04-10
> **OutCell said:**
> Thanks. acpi=off irqpoll worked! I'm in the live CD now.. Should i just install again like i did before?

Go ahead, see if this works. It should since you got to a live desktop this time.

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> Go ahead, see if this works. It should since you got to a live desktop this time.

Same as before.. I entering all details and install system but then it freezes at Partitions formatting at 5% with message below saying: Creating Ext3 file system for / in partition #1 of SCSI3 (0,0,0)...

And i think if i cold boot now like before i would get the same screen that i mentioned in my first post (initramfs).. :(

---

### Post by warp99 on 2008-04-10
Try manually partitioning the table first before you install. It's when you get to this part of the install:

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png)

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> Try manually partitioning the table first before you install. It's when you get to this part of the install:

[https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=5.png)

I think i tried that too but i will try it again and see what happens.. thanks for your continuous effort :)

---

### Post by warp99 on 2008-04-10
If that does not work you can download and manually partition the drive with a gparted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then finish the install with the Ubuntu alternative CD.

---

### Post by OutCell on 2008-04-10
> **warp99 said:**
> If that does not work you can download and manually partition the drive with a gparted LiveCD:

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Then finish the install with the Ubuntu alternative CD.

I just pulled out the Live CD i have (GParted) :) i will try that as well.. Thanks

---

### Post by OutCell on 2008-04-11
I get the disk as unallocated in GParted and when i try "New" to create a partition, i get a warning about msdos Disklabel on /dev/sda and then nothing happens and i am back to unallocated space..

this is weird

---

### Post by warp99 on 2008-04-11
Well at least we know what the problem is. Seems like Microsoft once again is over aggressive with it's installer. :lolflag: 

Why don't you try this. Boot to the install disc and run 'fdisk /dev/sda'. It's menu driven, but not to hard to figure out. See if we can delete the partition table, then recreate them with the correct linux partitions.

---

### Post by OutCell on 2008-04-11
> **warp99 said:**
> Well at least we know what the problem is. Seems like Microsoft once again is over aggressive with it's installer. :lolflag: 

Why don't you try this. Boot to the install disc and run 'fdisk /dev/sda'. It's menu driven, but not to hard to figure out. See if we can delete the partition table, then recreate them with the correct linux partitions.

Yeah Vista to be exact lool

Do you mean run the Live CD and then use a terminal and type fdisk /dev/sda? i didn't understand :P

---

### Post by warp99 on 2008-04-11
> **OutCell said:**
> Yeah Vista to be exact lool

Do you mean run the Live CD and then use a terminal and type fdisk /dev/sda? i didn't understand :P

That's correct. Run the terminal and then 'fdisk /dev/sda'.

---

### Post by OutCell on 2008-04-11
> **warp99 said:**
> That's correct. Run the terminal and then 'fdisk /dev/sda'.

Ok thanks :) will do that now

---

### Post by OutCell on 2008-04-11
Damned Vista and its none sense :(

I got this off the terminal after fdisk:

ubuntu@ubuntu:~$ sudo fdisk /dev/sda
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xf980de6f.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 19457.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help):

---

### Post by warp99 on 2008-04-11
Bingo. I think we have it. Print (p) the partition table and post the results.

---

### Post by OutCell on 2008-04-11
This is what i got:
Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf980de6f

   Device Boot      Start         End      Blocks   Id  System

Command (m for help):

---

### Post by buried on 2008-04-11
Manually create a partition (linux swap) with at least 1gb of swap space.

---

### Post by OutCell on 2008-04-11
> **buried said:**
> Manually create a partition (linux swap) with at least 1gb of swap space.
Thanks, i appreciate your help

Do you mean using the Partition Editor in the Live CD to create a swap partition first and then using the install button in the Live CD to install the system?

---

### Post by warp99 on 2008-04-11
According to this you have no partitions. First do a 'w' so fdisk can repair the errors to the DOS label then 'q'. Run 'fdisk /dev/sda1' again. Print the table, if any partitions are there then 'd' all of them. Now  let's create a partition for the /dev/sda1 then write it out. Let's 'n' to add the partition make it a primary partition, verify that we created it, then 'w' to write it out.

Once this is done close the terminal, reboot, and install Ubuntu as planned. Everything should be fine at this point.

Edit:
You can also create a swap partition if you want or just let the installer do it for you. It depends on you skills, so it's your choice.

---

### Post by OutCell on 2008-04-11
> **warp99 said:**
> According to this you have no partitions. First do a 'w' so fdisk can repair the errors to the DOS label then 'q'. Run 'fdisk /dev/sda1' again. Print the table, if any partitions are there then 'd' all of them. Now  let's create a partition for the /dev/sda1 then write it out. Let's 'n' to add the partition make it a primary partition, verify that we created it, then 'w' to write it out.

Once this is done close the terminal, reboot, and install Ubuntu as planned. Everything should be fine at this point.

Edit:
You can also create a swap partition if you want or just let the installer do it for you. It depends on you skills, so it's your choice.
Ok i think i tried 'n' before but i got confused with the options. I did it now and stopped at First cylinder, and i remember there was another option after this for another cylinder:
Command (m for help): p

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xca3d4d01

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): n
Command action
   e   extended
   p   primary partition (1-4)
p
Partition number (1-4): 3
First cylinder (1-19457, default 1):

---

### Post by warp99 on 2008-04-11
First delete 'd' any partitions that are on the drive. If there are none skip that part. Create a new parition 'n' make it primay 'p' then the partition number is 1 and the first cylinder is also 1 and the last cylinder is 19457. Verify this is correct  by printing the table 'p', then use the write command 'w' and exit. Reboot and install.

---

### Post by OutCell on 2008-04-11
> **warp99 said:**
> First delete 'd' any partitions that are on the drive. If there are none skip that part. Create a new parition 'n' make it primay 'p' then the partition number is 1 and the first cylinder is also 1 and the last cylinder is 19457. Verify this is correct  by printing the table 'p', then use the write command 'w' and exit. Reboot and install.

freezes at Partitions formatting  again, 5% with message below saying: Creating Ext3 file system for / in partition #1 of SCSI3 (0,0,0)...

I think the partition created with fdisk didn't get saved i don't know why! because when i started the install and manual partition there was sda and no sda1 :(

During the install i think swap was create but it is always the '/' mounting point that freezes..

---

### Post by warp99 on 2008-04-11
Well you're on the right track. Another program you can try is cfdisk. It does have a more graphical layout and may be a little easier to use. Same command string 'cfdisk /dev/sda'.  I'm pretty sure it's on the Ubuntu install CD. If not 'apt-get install cfdisk' since you can do that from the LiveCD as long as you have an internet connection.

---

### Post by OutCell on 2008-04-11
Thanks, will try that now but first let me try partitioning the drive with no '/' mount point. maybe it will work :P i just got a hunch

EDIT: Bad hunch, i need root :P
EDIT2: Still with same freezing problem :(

---

### Post by OutCell on 2008-04-11
same problem here
[http://ubuntuforums.org/showthread.php?t=687978&page=2](http://ubuntuforums.org/showthread.php?t=687978&page=2)

:(

---

