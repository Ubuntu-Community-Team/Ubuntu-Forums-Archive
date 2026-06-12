---
title: "Installing Ubuntu on dedicated partition"
date: 2012-12-14
forum: Installation &amp; Upgrades
---

### Post by rabot on 2012-12-14
Hi,
I have a big hdd which I have partitioned into 3, one is running Windows Xp, another is formatted to NTFS to store data only and the 3rd partition I've kept to install Ubuntu. That way the 2 OS reside on different partitions.

However, when I install Ubuntu, at what stage do I specify where I want to install it? I've tried but haven't found such an option and aborted the install.

There was one option in the beginning that offered to install Ubuntu alongside Windows for a dual boot. Where exactly would Ubuntu be installed, on the same partition as Windows?

---

### Post by papibe on 2012-12-14
Hi rabot.

You have to manually select in which partition Ubuntu will be installed. Since they are renamed to generic names (like /dev/sda1) make sure you can recognized the correct partition (by its size for example).

When is time to 'Allocate drive space', select 'Something Else'.

There you can specify not to touch (or format) your main Windows partition and select in which partition Ubuntu will be installed.

This youtube tutorial by quidsup is a good starting guideline: [How to use Partition Editor in the Ubuntu Installer]("http://www.youtube.com/watch?v=qBCHsgry2RQ").

I would recommend NOT resizing your main Windows partition, as in the tutorial, but just working on the second, and free NTFS partition.

Note that all this is available only on the ISO installation (not Wubi).

Remember that is always a good idea to backup your personal data, and have handy your Windows XP installation CDs... just in case.

Let us know how is goes.
Regards.

---

### Post by rabot on 2012-12-15
That youtube video was very helpful, thanks.
I picked the correct 'something else' option before but I forgot to create a swap space. This is what I did now and the installation went smoothly.

However, when I restarted the PC as requested, it boots directly to Windows. I don't even get the option of choosing which OS to boot from. So now I'm missing out completely on my beautiful Ubuntu installation. Is there any way to access it upon boot?

Also, when installing Ubuntu alongside Windows, is it installed within the same drive, really next to each other? Maybe I should have picked this option right from the beginning of the installation if I want to have this dual boot option?

---

### Post by darkod on 2012-12-15
Do you use UEFI boot or old legacy bios boot?

---

### Post by rabot on 2012-12-15
> **darkod said:**
> do you use uefi boot or old legacy bios boot?
uefi.

---

### Post by darkod on 2012-12-15
In that case you probably didn't install ubuntu in uefi mode too. You have to boot the cd/usb in uefi mode so that grub is installed correctly in uefi mode.

If it still has no option for ubuntu in the uefi boot manager, you might need to add the entry yourself.

---

### Post by Squirty on 2012-12-15
Isn't it possible to do this in your windows OS? 
(configuration screen -> system -> advanced system settings -> startup and recovery -> settings 
select the OS you want to use..) ---> only for windows vista and up


xp: 
change the boot.ini file
open command line, type "bootcfg /default / ID(#OS)"  probably this will be "bootcfg /default /ID2" if you have no more than 2 operating systems installed.

---

### Post by rabot on 2012-12-15
I inserted the cd to install windows and did the same to install ubuntu without making any changes to the BIOS. So I would expect both to be installed in UEFI mode?

When I go to Windows startup & recovery settings to select which OS is default, there is no Ubuntu in the drop-down...

---

### Post by rabot on 2012-12-15
I just reloaded the 'optimised' factory settings for the BIOS and now it says it supports both UEFI and legacy modes. Rebooted but went straight to Windows.

---

### Post by darkod on 2012-12-15
> **rabot said:**
> I inserted the cd to install windows and did the same to install ubuntu without making any changes to the BIOS. So I would expect both to be installed in UEFI mode?

When I go to Windows startup & recovery settings to select which OS is default, there is no Ubuntu in the drop-down...

I don't like working with assumptions. I have no idea how windows installs in uefi mode, but for ubuntu you have to use the 64bit version first of all, and make sure you boot the uefi dvd drive. On uefi boards there are uefi and legacy dvd boot devices listed. It's very easy to use the boot menu, or the boot order inside bios to select the correct device, instead letting it choose itself.

You can also use boot-repair to check the bootinfo, or do the recommended repair (I don't know if it will help, I'm not recommending it, only mentioning it).

And on top of all that, just because the board supports uefi it doesn't mean you are using it. But I guess you know whether you are using it or not. Have you tried creating ubuntu entry in the uefi boot manager?

---

### Post by oldfred on 2012-12-15
If you have UEFI, I do not think XP will work.

Windows (Vista 64, Windows 7 & Windows 8) only boots from gpt partitions with UEFI. 
And XP does not support gpt partitions.

---

### Post by rabot on 2012-12-16
I managed to fix it after a little bit of thinking and a lot of messing about. Here's how.

After doing a little bit of reading online about Ubuntu installation and partitioning, I realised that I didn't load the boot loader in the drive at the top level but within the partition where I was installing Ubuntu, due to ignorance. Because the computer was booting straight to Windows and there was no GRUB, that confirmed to me that it was not accessing the GRUB.

Since Ubuntu itself was installed without problem, I wanted to reinstall GRUB only. Found a few complicated ways to do it from the LiveCD since that was my only option, so I decided to reinstall Ubuntu all over again, making sure I install the bootloader in the correct place. 

Surprise surprise, the PC booted straight to Windows again. Full of patience, I reinstalled Ubuntu again from scratch, deciding to format the partitions first. This did not work well with the rather basic partition manager that is made available during the install, so I aborted, ran Ubuntu from the liveCD then ran gParted to tidy up the partions and then reinstalled Ubuntu for the second time. 

Upon reboot, no GRUB, goes straight to Windows. So I decided i had to manually install it from the liveCD. I restarted the PC from the CD and ran Ubuntu from it. Went online to find out how to exactly install GRUB. In the process, came across Boot Repair, got it installed and running in a few lines from the Terminal and it fixed everything. PC rebooted fine with GRUB after that.

Here are the results if you're interested:
[http://paste.ubuntu.com/1442109/](http://paste.ubuntu.com/1442109/)

I don't know why there are 5 partitons or sda in this report. sda1 runs Windows, sda2 should have Ubuntu, sda3 is for data and sda4 is for linux swap. In this report, sda2 is a mysterious unknown partition.

---

### Post by darkod on 2012-12-16
sda5 is your swap partition and it's logical. In linux the logical partitions get number 5 or higher, regardless how many primary partitions exist.
sda2 is the extended partition holding the logical partitions (in this case only sda5), so that is fine.

---

