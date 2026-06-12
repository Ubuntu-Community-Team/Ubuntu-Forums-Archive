---
title: "Install Live CD to USB as if it was a HDD!"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by abohsin on 2009-12-16
Hi everyone,

I have been using live cds for some time now, and have been happy with the default live-usb-creator utility provided by Ubuntu 9.10 specifically. However, due to the limitations of FAT32, no persistence can exceed 4GB. Therefore by running a simple google search, you find many solutions and utilities which help you create a FAT32 part for the Live CD files, and another partition (Ext2 usually) used for persistence (labeled) casper-rw. This you can also do manually without the need for any utils, nonetheless as soon as you perform a massive upgrade on the system, or perform several reboots, the usb fails to boot. However, i have to admit its performance is too good.

To cut it short, i decided to perform an installation direct to the USB (16GB SanCruzer), so i stumbled a few times. Each time I re-install because it is very slow during the navigation and all that. I re-installed without using swapfs, same issue. I formatted the partition using Ext2, Ext3, Ext4, but with no hope. I am currently trying XFS (don't know why, but not left with much options). So I want to ask two things:
1. What is the best FS Format for direct installations to USB?
2. Why are all the installations pausing like slow frames of a movie, they are not too slow, but they are definately annoying?

I also noticed that memory is not utilized, but CPU is very high.

Can someone provide me an explanation, without commenting that installations to USB is a rediculous idea, because seriously I think it is a great and practical idea.

Thanks in advance.

---

### Post by darkod on 2009-12-16
The idea is not ridiculous, and I don't know which FS is best for that, but I do know that transfer rate to usb stick/hdd is way slower then to int hdd. I believe that is why you say it's much slower. That's a fact.
Depending why you want it installed on usb stick, you might be able to live with that slow install, or maybe not. It's up to you.
Just as example, using the hdparm command if I measure the transfer to my internal 250GB 7200rpm 16MB cache Seagate, it says around 95MB/s. If I do the same to my ext usb hdd, WD 120GB Passport, it's around 25MB/s. Flash drive is approx the same speed, it depends slightly from stick to stick.
Get the picture?

---

### Post by abohsin on 2009-12-16
Yes I do get your point and i know it is valid. Nonetheless, there are some advantages of having a full installation on your USB, it basically acts as a laptop, with no peripherals. So basically you can shutdown your computer at work and walk home with all your needed apps and continue working from home, no need to perform dual installations on two machines. I know that I/O rate is much slower on USB Flash drives, but shouldn't it be slow only when you are attempting to read or write something? I don't think that navigation and opening of file browser or mozilla is an intensive, if at all, IO operation on the installed media.

Is there any way to tune the OS, or do something about this? Would XFS (which I am still testing) or reiserfs be any faster on USBs?

---

### Post by phillw on 2009-12-16
+1

As for any 'tweaks' you can do to speed things up a little, I'd suggest heading over to pendrivelinux.com -- They do some crazy things with memory-sticks ;-)

Phill.

---

### Post by abohsin on 2009-12-16
They are doing what I have tried before, creating FAT32 FS for the live cd folders and an ext2 for casper-rw with whatever size you pass, however 9.10 is not supported. I am currently downloading 8.04 and am going to test it with pendrivelinux to see if it is stable after linux-image and linux-kernel updates, or are the partitions somewhat disconnected from each other post the upgrade. But trust full installation is more advantageous.

But thanks for the comment man :)

---

### Post by Yvan300 on 2009-12-16
I had your same idea but here is what i did. The only difference is that i used an external hard drive. All i did was boot up virtualbox or in your case the live cd and started the install. After that i just choose my usb hard drive and it installed like any other internal hard drive . Oh and right before it begins installing, click advanced and choose to install grub on the flash drive and NOT your internal hard drive. It should boot fine afterwards.

---

### Post by phillw on 2009-12-16
> **abohsin said:**
> They are doing what I have tried before, creating FAT32 FS for the live cd folders and an ext2 for casper-rw with whatever size you pass, however 9.10 is not supported. I am currently downloading 8.04 and am going to test it with pendrivelinux to see if it is stable after linux-image and linux-kernel updates, or are the partitions somewhat disconnected from each other post the upgrade. But trust full installation is more advantageous.

But thanks for the comment man :)

I cheated, twice ...
1st Cheat - Used the LiveCD 9.10 to create a USB boot drive onto a 2GB usb drive that's certified as 'SpeedBoost' for Vista (Heck, it is now a spare drive)(It's in system --> Administration)
It takes care of the Casper-rw for you - possibly why pendivelinux aren't duplicating the instructions
2nd cheat - I ordered a 4GB drive from Canonica shop with 9.10 already on it & the kewl Ubuntu Logo on it.  

It's available here -->  [http://shop.canonical.com/product_info.php?products_id=577&osCsid=74fcf327742167e50adc31be57e51604](http://shop.canonical.com/product_info.php?products_id=577&osCsid=74fcf327742167e50adc31be57e51604)

Handy for doing installs, and certainly faster than running off the LiveCD if you want it portable.

Regards,

Phill.

---

### Post by abohsin on 2009-12-16
Yvan300, this is precisely what I did, but am experiencing slow performance post install. What version of Ubuntu were you using?

---

### Post by Yvan300 on 2009-12-16
9.10 kubuntu. But i used an external hard drive. Did you just let it choose the default options when the installer came up and also maybe you plugged your flash drive into one of the ports that are not usb 2.0. My laptop has 2 of them.

---

### Post by abohsin on 2009-12-17
Well people, my experience with installation is over, I have reached a conclusion, the magic word, believe it or not, is XFS. I formatted the USB as XFS (only the partition I want to use for installation, 6GB) then installed. Upon several reboots and a full day of heavy usage, the performance is more than impressive. It ALMOST seems as if it were installed on an internal HDD. At occasions it freezes for milliseconds, but it doesn't happen alot. Therefore, the ultimate answer, if anyone is willing to live this experience, is XFS. Bear in mind that during the installation to the USB, it takes a hell of alot of time to install, it takes from 4-6 hours.

At the end, I still prefer a live CD installation with persistence greater than 4GB. But it was fun installing to the USB straight forward.

Thank you everyone.

---

