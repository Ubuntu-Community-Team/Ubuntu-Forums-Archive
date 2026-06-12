---
title: "Question regarding existing partitions"
date: 2010-06-05
forum: Installation &amp; Upgrades
---

### Post by at0msk on 2010-06-05
I have Windows 7 installed on one of my boxes and want to install Ubuntu and dual boot between the two.

Currently I have one partition solely for Windows 7 (my OS partition). The second, and only other partition, is the rest of the HDD for programs, music, games, files, etc. The larger partition contains only a few folders designated to those areas mentioned previously (music, games, programs...).

If I were to install Ubuntu onto the OS partition (roughly 50GB available for use) along with Windows 7 what would I see or run into when I choose to boot into Ubuntu in regards to the second partition that has all mah stuffs?

---

### Post by darkod on 2010-06-05
Since you mention installing onto the win7 system partition, I guess you mean wubi install. Otherwise full ubuntu doesn't work on ntfs.
I would not rcommend installing wubi at all. Sooner or later you will run into issues, and you might even think ubuntu sucks because of them. I strongly suggest installing ubuntu as full install, on its own partitions, running on its own filesystem, the way it's supposed to be.
You don't have win7 installed inside another OS, right? So why install wubi inside windows...

You can test the live mode by booting with the ubuntu cd and selecting Try Ubuntu. That will run it from the cd and you can see what you like, and what you don't like.

If you still wish to install wubi, go ahead. But be advised that it was never designed to be long term install, just a quick try. And you can do a quick try using live mode from the cd, as mentioned.

It's up to you, but I would start thinking about a new partitioning plan, and to shrink one of the ntfs partitions to make unallocated space for a full ubuntu install.

As for seeing the second partition from wubi, usually you would be able to see that partition and read/write on it. But I don't use wubi and can't say for sure what it will look like.

---

### Post by kansasnoob on 2010-06-05
A true dual boot uses it's own partitions somewhat as shown here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=1)

Note: always use Win Vista and 7's own partitioning tool to resize itself!

This guide is somewhat more in depth:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

If you don't want to do any repartitioning you could use Wubi:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Also check out the faq's:

[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php)

Especially:

> 
Any gotcha?

Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.


Whatever method you decide on read this bug report before proceeding:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/576724)

---

### Post by Scunizi on 2010-06-05
I agree.. stay away from wubi.  It sounds like you've taken you main drive and split it into 2 partitions.... one for win7 and the other for additional data.  If you create a true dual boot you'll need 2 additional partitions at minimum for ubuntu (it will create them).  Personally I suggest 3 more partitions which really means 4 more partitions.  I'll explain.. a harddrive cannot have more than 4 primary partitions or sections. To make more than that one of the 4 primary partitions has to be an "extended" partition.  This allows the additional 3 to be created under it.  The 3 partitions you need to create are "root" known as "/", /swap and /home.  With 50 gigs available root should be about 8gigs, /swap at 2 gigs and the rest for /home.  /home is where your user created data lives.  Having a separate /home allows for easier reinstalls which inevitably happens when you start playing and messing with the system. It's new to you after all and you'll be looking at all kinds of How To's that may or may not be accurate.  

I also suggest using windows to carve out the 50 gigs you want to set aside.  Have it create it as an extended partition, no formatting necessary. When installing ubuntu you'll have to use the manual partitioning section of the install.. first you create your partition and size then assign it as root /swap or /home depending on which one you're creating.  Ubuntu will format it automatically.  If you have a choice of file system types choose either ext3 or 4.  I think 4 is the default.

As for how Ubuntu will see your "Data" partition.  It depends on what the file system is.. NTFS or Fat32 you'll still be able to get at it and use the data.

---

### Post by at0msk on 2010-06-05
Thanks for the information. I didn't now about the file system. I will create a partition for Ubuntu (no plans for using Wubi!). Will Ubuntu see the other partitions though? Or is this a potential partition nightmare?

Just about how big of a partition does Ubuntu need and can I split it off like I did Windows (OS part, files part)?

---

### Post by darkod on 2010-06-05
> **at0msk said:**
> Thanks for the information. I didn't now about the file system. I will create a partition for Ubuntu (no plans for using Wubi!). Will Ubuntu see the other partitions though? Or is this a potential partition nightmare?

Just about how big of a partition does Ubuntu need and can I split it off like I did Windows (OS part, files part)?

The recommendation of the previous poster about having separate /home is very good. But the choice is yours. Your personal files and settings go in your Home folder, which would be on a separate /home partition if it exists. That allows you to format / (the system partition, like C: in windows) and do a clean install but keeping all your data in /home untouched because you won't format it.

However the guided installs create only / + swap setup, you have to do manual partitioning if you want separate /home.

With separate /home you can have small / partition because most of your files will be in /home. In that case, even 10GB is enough for /.
For swap, if you plan regular hibernate you need approx 1.5 x RAM memory. If not, 2GB is enough.
The rest can go to /home. So, if you allocate 50GB for ubuntu, it would be 50 - 10 - swap (2GB).

First you will need to shrink one of your ntfs partitions for the 50GB. Use win7 Disk Management for that. Leave the new space as unallocated, don't create any partitions in it. Reboot win7 few times after the shrink, to do its disk checks.

After win7 is happy again, start the ubuntu installer, in step 4 select Manual Partitioning and in the unallocated space create the three mentioned partitions one by one, and all of them should be created as LOGICAL. In that case they will all take one extended partiion.

/ and /home can be ext4 filesystem, swap is swap
The mount points for / and /home are clear I guess, for swap also just swap.

And that's it. :)

PS. Yes, ubuntu will be able to see all of yours ntfs partitions and read files from them, also write files to them. I just don't recommend mounting ntfs partitions automatically, especially the C: partition. If you need access to them occasionaly, you can just open the partition you need when you need it. No need for auto mount.

---

### Post by at0msk on 2010-06-05
> **darkod said:**
> 

First you will need to shrink one of your ntfs partitions for the 50GB. Use win7 Disk Management for that. Leave the new space as unallocated, don't create any partitions in it. Reboot win7 few times after the shrink, to do its disk checks.

After win7 is happy again, start the ubuntu installer, in step 4 select Manual Partitioning and in the unallocated space create the three mentioned partitions one by one, and all of them should be created as LOGICAL. In that case they will all take one extended partiion.

/ and /home can be ext4 filesystem, swap is swap
The mount points for / and /home are clear I guess, for swap also just swap.

And that's it. :)

PS. Yes, ubuntu will be able to see all of yours ntfs partitions and read files from them, also write files to them. I just don't recommend mounting ntfs partitions automatically, especially the C: partition. If you need access to them occasionaly, you can just open the partition you need when you need it. No need for auto mount.

Thanks for the input. ;D I appreciate all the help. I'm so foggy when it comes to new things though. Can we take all that you said but remove Windows from the equation?

Scenario: 
20GB HDD freshly formatted in Windows to FAT32
Ubuntu 10.04 LTS CD (32 bit Desktop)
and...go! ;)

[COLOR=Gray][This is all assuming I have a working CD Rom drive, which I don't nor do I have a BIOS that supports booting to USB (please, no PLoP... :\) but let's just pretend. :) I wish there was a way I could slap this drive into an external enclosure with a USB interface and install Ubuntu onto it from another computer through USB using the CD.][/COLOR]

---

### Post by darkod on 2010-06-06
> **at0msk said:**
> 
Scenario: 
20GB HDD freshly formatted in Windows to FAT32
Ubuntu 10.04 LTS CD (32 bit Desktop)
and...go! ;)


Unfortunately I have to ask complicated questions again. :)

Are you sure that is 20GB separate HDD? I haven't heard of such. Because windows is calling partitions drives and that is very misleading.
If you only created 20GB FAT32 partition in windows, you need to delete it in Disk Management, and leave that space as unallocated.

Then boot with ubuntu cd and start the installer, and in step 4 just use the option Use Largest Available Free space. That will set it into the 20GB unallocated space. It doesn't work on fat32 or ntfs.

---

### Post by at0msk on 2010-06-06
> **darkod said:**
> Unfortunately I have to ask complicated questions again. :)

Are you sure that is 20GB separate HDD? I haven't heard of such. Because windows is calling partitions drives and that is very misleading.
If you only created 20GB FAT32 partition in windows, you need to delete it in Disk Management, and leave that space as unallocated.

Then boot with ubuntu cd and start the installer, and in step 4 just use the option Use Largest Available Free space. That will set it into the 20GB unallocated space. It doesn't work on fat32 or ntfs.


OK yeah that's what I meant. Sorry, long day. ;)

The 20GB HDD is an old laptop HDD in an external enclosure. The enclosure boasts a USB interface. I am now trying to use the Universal USB Installer linked on the Ubuntu download page but it does not see the drive (E:). The drive is currently FAT32 formatted. I'm not sure what's going on.

---

### Post by Scunizi on 2010-06-06
You've added a new wrinkle and complication with wanting to install ubuntu on the external usb drive.  The problem is doing a "normal" full install will put a new bootloader on your primary drive (internal).  If you happen to use a different usb port the system may see the drive as a totally different drive because of the location.  If you don't have enough space on your internal drive for the install you could use the Live usb creator built into ubuntu's live cd to install the live environment to the usb drive (be it a stick or enclosed external drive).  By installing in that fashion you won't mess with the windows boot loader.  On boot you'll have to set your bios to boot from usb first then the internal HD.  If the usb drive isn't plugged in then the system will automatically boot to the installed windows system.

---

### Post by darkod on 2010-06-06
> **at0msk said:**
> OK yeah that's what I meant. Sorry, long day. ;)

The 20GB HDD is an old laptop HDD in an external enclosure. The enclosure boasts a USB interface. I am now trying to use the Universal USB Installer linked on the Ubuntu download page but it does not see the drive (E:). The drive is currently FAT32 formatted. I'm not sure what's going on.

OK, now it's clear. :)

First of all, lets see whether it's recognized at all. Keep the 20GB disk plugged in, boot with the ubuntu cd in live mode, and in terminal do:

sudo fdisk -l (small L)

That will show all disks and partitions. So it should show two disks, your int disk and the 20GB, and the partitions on them. Post the results here anyway.

If that goes OK, I'll give you short instructions how to proceed.

---

### Post by at0msk on 2010-06-06
> **darkod said:**
> OK, now it's clear. :)

First of all, lets see whether it's recognized at all. Keep the 20GB disk plugged in, boot with the ubuntu cd in live mode, and in terminal do:

sudo fdisk -l (small L)

That will show all disks and partitions. So it should show two disks, your int disk and the 20GB, and the partitions on them. Post the results here anyway.

If that goes OK, I'll give you short instructions how to proceed.


OK thanks. I am working on that now....

It sees both.

I figured that I would just disconnect my desktop's SATA drive and connect my laptop hdd via USB and then throw the cd in. That way the only drive the installer would see is the laptop hdd. That worked and I did a full install and even updated. I knew that this would not work but I tried it anyway: I threw the laptop hdd back into the laptop and booted it up. I get the Ubuntu boot screen, hear a lil *duh-donk* noise and then just a black screen. :( Hey, I can dream can't I? I really want to get the OS onto this drive but can't really buy a new CD Rom for the laptop yet and PLoP is just a nightmare to try to use (laptop's BIOS doesn't support booting to USB devices).

Good news is that I successfully installed Ubuntu onto the drive and can boot to it on other computers. I really wanted to test Ubuntu's flexibility with regards to the installation process. I know with Windows I can start a gui install from another pc with the drive connected via USB and run a command with some switches and have the installer place the needed install files on the drive for installation then boot the drive up in the laptop and BAM windows installer. I was hoping I might find the same with Ubuntu.

---

### Post by at0msk on 2010-06-07
:)

---

### Post by darkod on 2010-06-07
I am starting to be confused what do you want to achieve. If the laptop can't boot from usb hdd, you can't run ubuntu from ext usb hdd on it, as you noticed.

One option would be to install grub2 to the MBR of the internal hdd, but in that case you will not be able to boot anything without the usb hdd connected, you should know that. If you are OK with that, you can try it.

Do you need the commands? If you do, please post the results of fdisk like I asked, with both disks connected. I hate guessing the partitions. :)

---

### Post by at0msk on 2010-06-07
> **darkod said:**
> I am starting to be confused what do you want to achieve. If the laptop can't boot from usb hdd, you can't run ubuntu from ext usb hdd on it, as you noticed.

One option would be to install grub2 to the MBR of the internal hdd, but in that case you will not be able to boot anything without the usb hdd connected, you should know that. If you are OK with that, you can try it.

Do you need the commands? If you do, please post the results of fdisk like I asked, with both disks connected. I hate guessing the partitions. :)

Sorry. :D To be clear there's only one HDD. I take it in and out of the laptop and external enclosure. So I put the HDD in the external enclosure, connected it to my desktop via USB and installed from the live CD. I then took the HDD out of the enclosure and placed it back into the laptop.

I figure that the boot record of the install is looking for something specific to the computer which was used to facilitate the install and that's why it won't boot up in the laptop. With the HDD in the laptop I can get the Ubuntu boot screen but after that I just hear a donk sound and am taken to a black screen. Maybe it's a video driver issue since the laptop's graphics card is not the same as the desktops?

Could I hack at the install until it likes the laptop?

---

### Post by darkod on 2010-06-07
OK, I understand now. Yes, it sounds video driver related.

Try this: leave the disk inside the laptop. Start the laptop and as soon as the BIOS screen is done start pressing Shift to see the grub menu. Because you have only ubuntu, it doesn't show the menu by default. You need to press Shift but before it actually starts loading ubuntu. :)

When the menu shows, highlight the main ubuntu entry but don't hit Enter, hit 'e' instead. It will show you few boot lines. With the arrows buttons and End button, go to the end of the line starting with linux. Delete quiet splash and add nomodeset.

Press Ctrl + X to boot. If that worked, connect the laptop to the internet, it's best with wired connection. Don't bother enabling wireless unless it works straight away.

Usually it will offer to install video driver if it found one. You can also look for a driver yourself by starting Hardware Drivers in System-Administration.

If nothing else works, there is a way to add the nomodeset parameter to be permanent, the above procedure is only temporary for one boot.

---

### Post by at0msk on 2010-06-07
> **darkod said:**
> OK, I understand now. Yes, it sounds video driver related.

Try this: leave the disk inside the laptop. Start the laptop and as soon as the BIOS screen is done start pressing Shift to see the grub menu. Because you have only ubuntu, it doesn't show the menu by default. You need to press Shift but before it actually starts loading ubuntu. :)

When the menu shows, highlight the main ubuntu entry but don't hit Enter, hit 'e' instead. It will show you few boot lines. With the arrows buttons and End button, go to the end of the line starting with linux. Delete quiet splash and add nomodeset.

Press Ctrl + X to boot. If that worked, connect the laptop to the internet, it's best with wired connection. Don't bother enabling wireless unless it works straight away.

Usually it will offer to install video driver if it found one. You can also look for a driver yourself by starting Hardware Drivers in System-Administration.

If nothing else works, there is a way to add the nomodeset parameter to be permanent, the above procedure is only temporary for one boot.

Thanks! I hate that I am at work now. Other than the wife and dog I have a reason to feel giddy about getting home! haha I will try this straight away and report back. Won't be until after 3PM EST though.

---

### Post by at0msk on 2010-06-07
Just in case, where does Ubuntu put and look for drivers? Maybe I can get the driver files I need and just place them in the directory. :KS

---

### Post by darkod on 2010-06-07
> **at0msk said:**
> Just in case, where does Ubuntu put and look for drivers? Maybe I can get the driver files I need and just place them in the directory. :KS

I don't think it can work that way, and I have no idea where it puts them.

---

### Post by at0msk on 2010-06-07
OK Thanks. Well all I have to say is "!!!!!!!!!"

I am posting from my Ubuntu laptop. Although it hasn't found a graphics driver and my packages are all up-to-date. I don't know what to expect when I reboot. Should I change **nomodeset **back to **splash**? Where should I look for a driver? Should I use conventional means like I would when on a Windows install? Or do I need to look for a linux variant?

---

### Post by darkod on 2010-06-07
> **at0msk said:**
> OK Thanks. Well all I have to say is "!!!!!!!!!"

I am posting from my Ubuntu laptop. Although it hasn't found a graphics driver and my packages are all up-to-date. I don't know what to expect when I reboot. Should I change **nomodeset **back to **splash**? Where should I look for a driver? Should I use conventional means like I would when on a Windows install? Or do I need to look for a linux variant?

If you followed my advice, that was only one time change. On next reboot it will be gone. My suggestion:

To make sure the nomodeset parameter is helping, reboot and try to boot normal, without any editing. If that fails, try again with adding nomodeset as you already did.

Let me know how it worked out, and while you are still booted in your laptop ubuntu, I'll tell you how to make it permanent so you don't have to edit on every boot.

---

### Post by at0msk on 2010-06-07
> **darkod said:**
> If you followed my advice, that was only one time change. On next reboot it will be gone. My suggestion:

To make sure the nomodeset parameter is helping, reboot and try to boot normal, without any editing. If that fails, try again with adding nomodeset as you already did.

Let me know how it worked out, and while you are still booted in your laptop ubuntu, I'll tell you how to make it permanent so you don't have to edit on every boot.

OK I will try that. 

I found [http://ubuntuforums.org/showthread.php?t=190022](http://ubuntuforums.org/showthread.php?t=190022) by searching however my xorg.conf file is empty?

Nah, needed to set **nomodeset**...

---

### Post by darkod on 2010-06-07
You will need to add it in /etc/default/grub. Open it with:

gksudo gedit /etc/default/grub

Find the line

GRUB_CMDLINE_LINUX=""

and change it to

GRUB_CMDLINE_LINUX="nomodeset"

In that line you can add any parameter you want to set manually. Save and close the file. To update grub.cfg run:

sudo update-grub

Restart and ubuntu should boot without your intervention.

---

### Post by at0msk on 2010-06-07
> **darkod said:**
> You will need to add it in /etc/default/grub. Open it with:

gksudo gedit /etc/default/grub

Find the line

GRUB_CMDLINE_LINUX=""

and change it to

GRUB_CMDLINE_LINUX="nomodeset"

In that line you can add any parameter you want to set manually. Save and close the file. To update grub.cfg run:

sudo update-grub

Restart and ubuntu should boot without your intervention.

OK. I'll try that. Looks like the xorg.conf file is owned by root and I cannot do anything with it. What do I do? I certainly need a video driver. :D

well it went through two reboots ok but a later third one left me needing to type in nomodeset again. I checked grub.cfg and that line is still what I left it as (GRUB_CMDLINE_LINUX="nomodeset"). There's a GRUB_CMDLINE_LINUX_DEFAULT line which is set to splash...

---

### Post by at0msk on 2010-06-08
to the top! :guitar:

---

### Post by at0msk on 2010-06-08
:\

---

### Post by darkod on 2010-06-08
If nomodeset is there, that is replacing having to type it on every boot. I'm confused.

It still doesn't work?

---

### Post by at0msk on 2010-06-08
> **darkod said:**
> If nomodeset is there, that is replacing having to type it on every boot. I'm confused.

It still doesn't work?

It works but some times it doesn't. On some random reboots I have to set nomodeset again but if i reboot right after that it works...

---

