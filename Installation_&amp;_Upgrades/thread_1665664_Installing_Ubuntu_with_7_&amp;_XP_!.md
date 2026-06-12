---
title: "Installing Ubuntu with 7 &amp; XP !"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by Tom_T on 2011-01-12
Hi
New hardisk, just installed 7 as I need it for work.
I also need XP, but would prefer Ubuntu.

So how do I add XP & Ubuntu to the system and keep 7 ?

A nice trible boot menu would help !!

Thanks

---

### Post by Quackers on 2011-01-12
How many partitions is Windows 7 using? Please have a look in (or post a screenshot of) the Windows disk management screen.

---

### Post by ve3tru on 2011-01-12
The best way is using virtual box
I have had multiple OS in the past and if you like spending a lot of time fixing things then its right for you. The problem with multi OS is, each OS is updating all the time, at some point they conflict with the other OS.Even if you try to monitor what gets updated they slip by you. Each OS wants control, in fact MS will delete files thinking Linux is a virus I think it does that deliberately the profit motive. Virtual box and there is another one cant remember they are free and work good.

---

### Post by moorebounce on 2011-01-12
I read and done this myself. It's best to install XP first. I used a program (EASEUS Partition Master Home Edition) to create partitons for my XP and Windows7. Then I installed Ubuntu. It worked great for me.

---

### Post by Tom_T on 2011-01-12
7 has created 2 partitions. 

One is around 100mb, the other is using the rest of the disk.

Would I be better factory restoring XP, then 7, then ubuntu ?
Thanks

---

### Post by Quackers on 2011-01-12
I would definitely install Ubuntu last (keeping an eye on not exceeding 4 primary partitions! or 3 and an extended) but as for XP or Win 7 first/second, I'm not sure. 
Maybe somebody could offer advice on that :-)

---

### Post by 1492 on 2011-01-12
My guess would be that you should install 7 first because on the MS forums there are suggestions to people trying to run XP programs on 7 that they should dual-boot XP & 7, so that way probably works fine.

---

### Post by oldfred on 2011-01-12
Win7 creates the extra 100MB boot/recovery partition so you can encrypt the main partition. It will install in one partition if it exists in advance. You need to use NTFS primary partitions for both copies of windows. Windows normally moves the boot files from the second install to the first install that has the boot flag. It is the only way windows can boot two installs. If independent, grub can boot both:

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by Tom_T on 2011-01-13
Thanks for the advice.
Reading some of the threads linked, It appears I should create 3 primary partitions.

Install XP, remove the boot flag,
Install 7
Install Ubuntu 

And hopefully I should be able to boot and of the 3 OS's from grub !!

Any comments etc ??

Thanks

---

### Post by oldfred on 2011-01-13
The extended partition consumes one primary partition. You can install all of Ubuntu in logical partitions. I would also create a shared NTFS partition for  any data you want to share between all three systems.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by ottosykora on 2011-01-13
I have w7, xp, ubuntu, fedora, debian, w98se on same disk working happy with each other.

The convenient way in such setup is to have either some commercial boot manager doing all that hide-unhide operations , or rather stable is also using grub in a separate small partition. This acn be at the end of the drive.

Older windows need to be placed in primary partition, take that for windows and the rest as ubuntu, data etc can live in volumes in extended.

If yousing grub, you have to take also care that the windows system partitions are hiden when not in use, only the one used now is active.
So nothing will be mixed up.

In any case, it is convenient to install xp first, then w7 and then ubuntu.

Installing xp after w7 can be a pain.

And make sure you have the proper sata drivers ready when installing xp on new computer. xp does not have sata drivers included!
You can set some bios to ide mode, but then again your w7 will refuse to boot unless you install ide drivers to it.

---

### Post by Tom_T on 2011-01-13
Thanks
I have an XP recovery DVD that will reload everything, inc the SATA drivers.
Once I re installed XP, I'll use Gparted to resize and then 7..

Thanks

---

### Post by Tom_T on 2011-01-13
Hi
I have the factory recovery DVD so putting XP on is very simple.
I'll do that, then use GParted to resize and create the extra primary partitions.
Then 7 !!

Fun weekend ahead,,,

---

### Post by Tom_T on 2011-01-13
Hi
I have the factory recovery DVD so putting XP on is very simple.
I'll do that, then use GParted to resize and create the extra primary partitions.
Then 7 !!

Fun weekend ahead,,,

---

### Post by Tom_T on 2011-01-13
Sorry for the duplicate posts !
My Laptop decided to have a moment

---

### Post by ledzpg on 2011-01-13
I used to have Win 7, XP and OpenSUSE on a tri-boot config.

What I did was:

1) Install XP
2) Install Win 7
3) Install OpenSUSE keeping an eye on the grub location.
I've installed it directly on the Linux partition, keeping the MBR with the Win 7 boot loader.

After that, I've used [Vista Boot Pro]("http://www.vistabootpro.org/") to add an entry to the grub located at the Linux partition, and then I was able to use both boot loaders at the same time, mainly the MS one.
When I choose OpenSUSE on the menu, it shows me the grub menu, with an windows entry, so I was able to switch back to Windows if I needed.

I just don't know how to select the boot loader installation on Ubuntu, never tried to change it, but shouldn't be so difficult.

I'll find a picture here of my old boot loader to attach here...

---

