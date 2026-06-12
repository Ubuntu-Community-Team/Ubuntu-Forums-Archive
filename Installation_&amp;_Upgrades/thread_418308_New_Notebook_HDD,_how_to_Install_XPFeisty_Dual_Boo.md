---
title: "New Notebook HDD, how to Install XP/Feisty Dual Boot"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by joshjani on 2007-04-22
I have been reading many posts trying to figure this out, but as a new user of Linux and Ubuntu, I'm more confused than ever.

I wish to install Ubuntu on my laptop as a dual-boot with XP Home. I am, however, also upgrading from a 40GB HDD to a 100GB. I want to keep my XP install as-is, with all my programs, settings, etc, so I will be cloning my XP drive to the new drive.

My question is how best to handle the partitioning. When I get my new drive, do I create 2 or more partitions, clone XP to one, then install Feisty on the other, or do I just clone XP however XP wants to, with one big partition, then let the Feisty install handle making the proper partitions, using the space available?

Whenever I've purchased new hard drives or upgraded in the past for my XP machines, I've always just used NTFS and made one big partition, installing XP to that. But I've read all over here that XP does not like you resizing its partitions to install Ubuntu. Then I've also read to just defrag my windows HDD and install Ubuntu from the CD, letting it handle the partitioning, at most just telling Ubuntu how much space to use.

I would basically like to divide the new drive in half, give half to XP and half to Ubuntu, and keep my XP as-is. Having a place where I can put both XP and Ubuntu files wouldn't be bad, either, but only if it's not too difficult!

Anyone with an easy step-by-step for this? Thanks
JC

---

### Post by pepsi_max2k on 2007-04-22
Given that XP isn't set up to use any other partitions at the moment, and i'm not sure how well it does imaged to a drive with a different partition set up, maybe just creating a single partition and mirroring to that first could be best. Then again, it would prolly be fine either way... As you've got a backup for the image you can always try again if it don't work first time. Something like Acronis DiskDirector should resize it OK if you install windows first, I've done it before with a Windows 98 partition (and possibly XP...).

Whatever you do, you wanna end up with at least 3 partitions. One small one (about the size of your ram) at the start of the drive for Ubuntu's Swap partition, one for windows and one for ubuntu. I'd suggest making these first and then just telling ubuntu to mount to and re-format these when installing, saves getting confused over which partition is which and messing things up :p. Read the following thread for more advanced partition setups:

[http://ubuntuforums.org/showthread.php?t=416981](http://ubuntuforums.org/showthread.php?t=416981)

---

### Post by joshjani on 2007-04-23
> **pepsi_max2k said:**
> Given that XP isn't set up to use any other partitions at the moment, and i'm not sure how well it does imaged to a drive with a different partition set up, maybe just creating a single partition and mirroring to that first could be best. Then again, it would prolly be fine either way... As you've got a backup for the image you can always try again if it don't work first time. Something like Acronis DiskDirector should resize it OK if you install windows first, I've done it before with a Windows 98 partition (and possibly XP...).

Whatever you do, you wanna end up with at least 3 partitions. One small one (about the size of your ram) at the start of the drive for Ubuntu's Swap partition, one for windows and one for ubuntu. I'd suggest making these first and then just telling ubuntu to mount to and re-format these when installing, saves getting confused over which partition is which and messing things up :p. Read the following thread for more advanced partition setups:

[http://ubuntuforums.org/showthread.php?t=416981](http://ubuntuforums.org/showthread.php?t=416981)

Thaks for the reply, but more advanced is not what I need! I'm pretty nervous about attempting this, as what I've done in the past has not involved making multiple partitions, primary OR extended!:confused: 
I want both XP and Ubuntu to run the best that they can; I like the idea of having a partition that both Ubuntu and XP can use. But I don't know whether to give these partitions I make drive letters, for instance, since I want to copy XP as is. 

So far all I've done is plug the new drive into an external case. I know how to make partitions in Windows, but I'm still unsure of my first step, because I'm sure I can't make an ubuntu-ready partition within windows.
I downloaded and made a Live CD of Gparted- will it see the USB drive, especially if it has a windows format partition on it?

---

### Post by icechen1 on 2007-04-23
> **joshjani said:**
> I have been reading many posts trying to figure this out, but as a new user of Linux and Ubuntu, I'm more confused than ever.

I wish to install Ubuntu on my laptop as a dual-boot with XP Home. I am, however, also upgrading from a 40GB HDD to a 100GB. I want to keep my XP install as-is, with all my programs, settings, etc, so I will be cloning my XP drive to the new drive.

My question is how best to handle the partitioning. When I get my new drive, do I create 2 or more partitions, clone XP to one, then install Feisty on the other, or do I just clone XP however XP wants to, with one big partition, then let the Feisty install handle making the proper partitions, using the space available?

Whenever I've purchased new hard drives or upgraded in the past for my XP machines, I've always just used NTFS and made one big partition, installing XP to that. But I've read all over here that XP does not like you resizing its partitions to install Ubuntu. Then I've also read to just defrag my windows HDD and install Ubuntu from the CD, letting it handle the partitioning, at most just telling Ubuntu how much space to use.

I would basically like to divide the new drive in half, give half to XP and half to Ubuntu, and keep my XP as-is. Having a place where I can put both XP and Ubuntu files wouldn't be bad, either, but only if it's not too difficult!And DOn't forget to defragment your drive!

Anyone with an easy step-by-step for this? Thanks
JC
First,BACKUP all your important files,you will never know when it can go wrong.
Then use a program like partition magic,GPARTED(included in ubuntu live cd),or other to make partition.I am not sure what to ddo but you need to resize your XP partition and the freed space ,you need to format it to a EXT3 et a 500 mb SWAP(it depend how much RAM you have) format and in ubuntu installer,use the avanced option and choose the new partition.Hope THis Help!

---

### Post by joshjani on 2007-04-24
Got it to work! I can now boot flawlessly to either ubuntu feisty or WinXP Home!

How I did it: Not really a how-to, since I didn't really know what I was doing as I went along, but seems pretty simple in hindsight.

As I wanted to upgrade my hard drive at the same time I was going for this dual boot, I placed the new notebook drive in an external USB 2 case. The external After many false starts with XP's xcopy command, I finally made an exact copy of my hard drive to the external using a tool I got free from Seagate, Disk Wizard, which is made by Acronis. Seagate has all the Maxtor software there, too. I've read that the software might require that you have at least one either Seagate or Maxtor drive in the system. I had a Seagate original, with a Toshiba destination drive, but in a Maxtor case(!) Anyway, I'm not sure about drive requirements, but the Seagate application couldn't have made it any easier. It cloned the drive and made the new one bootable, with one big XP NTFS partition. Replaced my original with the new, bigger drive, and, after checking my C drive, XP booted right up. Yay!

Then I took my Live CD of Feisty and popped it in, rebooted, and began the install. I was asked how I wanted the partitions, I chose the first option "Guided", where there was a slider to let me resize the original partition to the size I wanted, installing ubuntu to what was left. I chose to keep 60gb for XP, leaving 38+ for ubuntu. After a relatively short time, I had three partitions on the drive, one made by XP, two made by ubuntu, and a clean fresh install of feisty. 

One more reboot, and I now have a choice screen when booting, where booting to ubuntu's various options come first, with XP at the bottom of the list. Super happy!:) 

My only tiny thing now is whether I can move XP up in the list, and whether I can have the boot option last a little longer. Right now, if I don't hit a key in 5 sec, it boots right to ubuntu. Ultimately, I'd like it to list Ubuntu first, XP second, and the rest after that, and I'd like the boot option screen to last about 20sec before auto-continuing.

But, this plus getting my Broadcom card to work, I've had an ubuntu-licious day!

---

### Post by confused57 on 2007-04-24
Impressive job getting your system working...this link should answer your grub questions:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by pepsi_max2k on 2007-04-25
> **joshjani said:**
> My only tiny thing now is whether I can move XP up in the list, and whether I can have the boot option last a little longer. Right now, if I don't hit a key in 5 sec, it boots right to ubuntu. Ultimately, I'd like it to list Ubuntu first, XP second, and the rest after that, and I'd like the boot option screen to last about 20sec before auto-continuing.

very easy. open /boot/grub/menu.lst (you may have to open a root file browser from command line (gksudo nautilus) to edit it. there's a list of os's in there all starting "title NAME_OF_OS" followed by their load commands. whatever position these are in the file is the same position you'll see when grub starts (you only see the title bits, and you can change the name to whatever).

at the top of the files there's variables like "default" and "timeout" followed by numbers. guess which one you change for the auto boot timing? and default coresponds to the order of the following OSs in the file, so whatever comes first is 0, second in the list is 1, etc. change the number to change what OS you want selected for auto booting, or set it to "savedafault" (i think) for it the use whatever you last booted at default (check google for more about that).

---

