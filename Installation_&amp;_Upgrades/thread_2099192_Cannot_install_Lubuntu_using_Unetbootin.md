---
title: "Cannot install Lubuntu using Unetbootin?"
date: 2012-12-28
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2012-12-28
Hi guys. Recently tried Ubuntu. Loved it. However I've decided to use Lubuntu because it's lightweight. What I did.

1. Backed up my 8GB usb thumb drive to my Windows 7 partition on hard drive.

2. Formatted 8GB thumb drive using GParted.

3. Since I'm doing all this on Ubuntu OS, I downloaded Unetbootin for Linux, ran it from /home/user/downloads , loaded the Lubuntu ISO, target was the USB drive.

4. Turned off laptop. Went to BIOS. Set thumb drive as first boot. Restarted.

5. Got the Unetbootin window, a countdown is running, but the only option is "Default". Pressed enter, the countdown repeats all over again.

By the way, in number 3, it all happened really fast, like less than 5 seconds (?).  Could that be the problem?

Please help.
Thank you =)

---

### Post by vasa1 on 2012-12-28
> **KayeNg said:**
> ...
By the way, in number 3, it all happened really fast, like less than 5 seconds (?).  Could that be the problem?
...
I think so. There's a slight lag at one point and if you didn't see that lag then something's wrong. Did you do the checksum thing to verify your download?

---

### Post by KayeNg on 2012-12-29
> **vasa1 said:**
> I think so. There's a slight lag at one point and if you didn't see that lag then something's wrong. Did you do the checksum thing to verify your download?

Hi there, yes I did the md5sum in Terminal.  It's correct. Please help.

---

### Post by 2F4U on 2012-12-29
Since you are creating the usb drive from within Ubuntu, is there any special reason to use unetbootin instead of Startup Disk Creator, which comes with Ubuntu? I am asking since I myself always have problems when I use unetbootin and it is mostly hit and miss for me.

---

### Post by KayeNg on 2012-12-29
> **2F4U said:**
> Since you are creating the usb drive from within Ubuntu, is there any special reason to use unetbootin instead of Startup Disk Creator, which comes with Ubuntu? I am asking since I myself always have problems when I use unetbootin and it is mostly hit and miss for me.

Hey guys, problem solved. I'm not sure but it may have been the usb drive. Using Gparted, I made a thorough sweep of it. Deleted the partition then made a new fat32, as opposed to what I did earlier which was merely formatting the drive.  I'm not entirely sure but it did do the trick. I proceeded to use Startup Disk Creator as you suggested. Everything went well.

Anyway, couple of questions though. When I was using Gparted to format the partition in my hard drive for Lubuntu installation, why was there a 5 or 6 GB used space left? I deleted the partition, resized, and created a new partition--same thing. There's always that 5 or 6 GB used space, even after formatting.  Is this normal? 6 GB is a lot of space.  I'm kind of finicky, I want everything to be 'perfect'.  Did something go wrong? Or was it just a Gparted bug? Despite that, everything seems to be working ok. I'm just curious.

Also, same thing with my usb thumb drive.  There was that 1MB used space that refused to go away even after deleting and formatting via Gparted.

Thanks guys!!!

---

### Post by sudodus on 2012-12-29
I think that the used space indicated is space in the partition used by the file system to organize itself (file allocation table, journaling (in ext3, ext4, ntfs ...) etc.

---

### Post by KayeNg on 2012-12-29
> **sudodus said:**
> I think that the used space indicated is space in the partition used by the file system to organize itself (file allocation table, journaling (in ext3, ext4, ntfs ...) etc.

I'm an idiot so I'm not sure what you mean by that, but are you saying the "used space" was not wasted by any means? It's not sitting in the partition doing absolutely nothing right now, is it?
Because I want to make use of every inch of the partition....
Thanks!!!

---

### Post by sudodus on 2012-12-29
> **KayeNg said:**
> I'm an idiot so I'm not sure what you mean by that, but are you saying the "used space" was not wasted by any means? It's not sitting in the partition doing absolutely nothing right now, is it?
Because I want to make use of every inch of the partition....
Thanks!!!
Yes, I think it is used. It is normally a small fraction of the partition size (small partition <--> small space used initially, big partition <--> big space used initially).

Sometimes there is also unallocated space outside the partitions. Gparted is smart enough to select start and end of partitions at suitable places (multiples of bytes, kB, MB). Also it leaves some space at the beginning of the drive for booting and mounting data.

I'm happy with the way Gparted creates partitions and file systems.

---

### Post by KayeNg on 2012-12-29
> **sudodus said:**
> Yes, I think it is used. It is normally a small fraction of the partition size (small partition <--> small space used initially, big partition <--> big space used initially).

Sometimes there is also unallocated space outside the partitions. Gparted is smart enough to select start and end of partitions at suitable places (multiples of bytes, kB, MB). Also it leaves some space at the beginning of the drive for booting and mounting data.

I'm happy with the way Gparted creates partitions and file systems.

The partition I created for Lubuntu is 400GB (leaving 100GB only for Windows, because I hate it).  So you're saying the 5 to 6 GB "used space" created by GParted is normal, right? (big partition <--> big space used initially, like you said)

Gotcha. Thanks for your time! Really appreciate it guys. =D

---

