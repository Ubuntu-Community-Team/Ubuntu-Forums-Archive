---
title: "Which filesystem for Linux on a slow USB stick ?"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by Lockheed on 2014-10-31
I am making an emergency OS usb stick out of SanDisk Fit. It is great because it's tiny, but it is also very slow.

What filesystem would be best for the OS installed on such slow medium? I narrowed it down to those three, but am open to suggestions if there's something better:

&#10148; BTRFS with zlib compression - because data written is compressed and hence there is less of it to write
&#10148; ext4 with disabled journaling - because it has no journalling
&#10148; f2fs - because it is designed for flash devices

I already installed a system with BTRFS lzo/zlib, but if I install a package and try to use a browser, the system becomes partially unresponsive, which I suppose is the fault of overloaded I/O of the usb stick.

Would another filesystem make things better?

---

### Post by MartyBuntu on 2014-10-31
You're completely at the mercy of your USB's read/write speeds. File system types will have, for all intents and purposes, no perceptible difference.

But this is an "emergency OS", so none of this should matter...

---

### Post by Lockheed on 2014-10-31
This is incorrect. Please, read again the BTRFS option. Transparent compression increases the effectual read/write speeds.

On my HDD, with ext4 I used to get up to 60MB/s read/write speeds. With BTRFS zlib compression the same HDD gives me up to 250-300MB/s.

---

### Post by matt_symes on 2014-10-31
Hi

> emergency OS usb

I take it this is not going to be a bootable USB ?

Kind regards

---

### Post by Lockheed on 2014-10-31
It is. 
Partition layout is like so:
23GB fat32 / 8GB linux with grub (for f2fs there will be additional ext2 partition for /boot)

---

### Post by matt_symes on 2014-10-31
Hi

> **Lockheed said:**
> It is. 
Partition layout is like so:
23GB fat32 / 8GB linux with grub (for f2fs there will be additional ext2 partition for /boot)

I'm not going to offer any suggestions as to which filing system to run as my choices would have been similar to yours. I would suggest you run metrics to see which one is faster but there are some steps i would take to try to speed it up.

I would try to identify if BTRFS was CPU or I/O bound when reading from the stick with lzo compression as i would have expected the compression to make the read and the writes to the stick faster due to the smaller size. If it's still I/O bound then compression would not seem to be making that much difference. The compression ratio on binaries is generally much lower than for text files.

I would also try to mount as much of the filing system as possible as RAM disks, such as /var/log. Anything that gets written to frequently. You could mount application configuration files as RAM disks and copy the contents to them at startup. You can write them back to the stick at shutdown.

Disable any unnecessary writes to the stick such as extX updating atime values.

In a way MartyBuntu is correct when he states that you are at the mercy of the maximum transfer rate of the USB stick. USB transfer speeds have a maximum limit.

However, if you can compress as much as possible, thereby offsetting I/O for CPU usage, and run as much as possible from RAM then that should help the situation.

Kind regards

---

### Post by fantab on 2014-10-31
BTRFS is not stable enough yet (its a work in progress) to work as 'emergency' option.
IMO EXT3 will have an overall better performance, but as mentioned earlier 'you are at mercy of your USB drives read/write speeds...

Do you want a bootable Live Ubuntu, where you just write the Ubuntu.iso to USB? OR
Do you want to install Ubuntu on the USB drive?

The second option will be faster compared to the former.

---

### Post by matt_symes on 2014-10-31
Hi

> BTRFS is not stable enough yet (its a work in progress) to work as 'emergency' option.

I don't agree with this if the OP's meaning of the word 'emergency' is similar to mine when applied to this use case.

Being an emergency option, it will hardly be used, not regularly updated and i think, in this instance, it should be stable enough.

Personally, i have had no real issues with BTRFS that were not fixable, although i do keep regular backups. My Fedorda installation uses BTRFS and you have to remember that Oracle and OpenSUSE both use BTRFS.

You could argue that extX without journaling is an accident waiting to happen.

Opinions do differ though and yours, although different than mine, is a valuable perspective.

Kind regards

---

### Post by MartyBuntu on 2014-10-31
> **Lockheed said:**
> With BTRFS zlib compression the same HDD gives me up to 250-300MB/s.

Benchmark that and throw up some screenshots.

I'd like to see it.

---

### Post by sudodus on 2014-11-01
> **Lockheed said:**
> I am making an emergency OS usb stick out of SanDisk Fit. It is great because it's tiny, but it is also very slow.
...

I suggest that you get a faster USB pendrive. Particularly the ability to write 'many small files' can make a big difference. See these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

[Link to USB 3.0 Flash Drive Speed Tests]("http://usb.userbenchmark.com/")

**[Link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085")**

---

### Post by Lockheed on 2014-11-01
> **matt_symes said:**
> I would also try to mount as much of the filing system as possible as RAM disks, such as /var/log. Anything that gets written to frequently. You could mount application configuration files as RAM disks and copy the contents to them at startup. You can write them back to the stick at shutdown.
Excellent point. I have not thought of it before.

I went with BTRFS zlib for maximal compression and - because I am using Arch - Anything-sync-daemon which works very well. I still get some hiccups but I think it is tolerable considering the medium. 
But I lost too much time on it already to try to run tests on other filesystems.



> **fantab said:**
> BTRFS is not stable enough yet (its a work in progress) to work as 'emergency' option.
I&#8217;ve been using BTRFS exclusively on my main workstation and for my data disks since a year. I do a lot of things with it, and never had an issue which was not my fault.
If I am not mistaken, BTRFS has been officially pronounced as &#8220;production ready&#8221; several months ago. Facebook has been using BTRFS for its data centers since then.

> **MartyBuntu said:**
> Benchmark that and throw up some screenshots.
I'd like to see it.
Why don&#8217;t you do your own tests? I think it will be more convincing, valuable and applicable to you.


> **sudodus said:**
> I suggest that you get a faster USB pendrive. Particularly the ability to write 'many small files' can make a big difference.
I am aware of the speed difference, but for me it is not worth it to replace [this]("http://www.gadgetguy.com.au/cms/wp-content/uploads/SanDisk-Cruzer-Fit-hands-on-02.jpg") with [this]("http://i.ytimg.com/vi/Af3BEcmUDtM/maxresdefault.jpg").

---

### Post by sudodus on 2014-11-01
Well, if it is important to keep the pendrive small, another option is that of *terminator14*'s RAM method. See this link
[URL="http://ubuntuforums.org/showthread.php?t=1594694"]
Making Ubuntu Fast using RAM (updated and simplified)[/URL]

---

### Post by kurt18947 on 2014-11-01
> **Lockheed said:**
> Excellent point. I have not thought of it before.

I went with BTRFS zlib for maximal compression and - because I am using Arch - Anything-sync-daemon which works very well. I still get some hiccups but I think it is tolerable considering the medium. 
But I lost too much time on it already to try to run tests on other filesystems.




I&#8217;ve been using BTRFS exclusively on my main workstation and for my data disks since a year. I do a lot of things with it, and never had an issue which was not my fault.
If I am not mistaken, BTRFS has been officially pronounced as &#8220;production ready&#8221; several months ago. Facebook has been using BTRFS for its data centers since then.


Why don&#8217;t you do your own tests? I think it will be more convincing, valuable and applicable to you.



I am aware of the speed difference, but for me it is not worth it to replace [this]("http://www.gadgetguy.com.au/cms/wp-content/uploads/SanDisk-Cruzer-Fit-hands-on-02.jpg") with [this]("http://i.ytimg.com/vi/Af3BEcmUDtM/maxresdefault.jpg").

I guess its a matter of what's most important to you size vs. speed. There are some USB 3.0 flash drives that when plugged into a USB 3.0 port approach spinning drive R/W performance but they're full sized. USB 2.0 is going to be the limitation with the faster USB flash drives.

---

### Post by oldfred on 2014-11-01
While normally I would not suggest ext4 without journal on a small drive fsck does not take long and as an emergency boot drive removing journal helps speed. So for my emergency boot flash drive I use ext4, turn off journal and use noatime.

  Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Post #14 some flash drives that did not work
[http://ubuntuforums.org/showthread.php?t=2120196](http://ubuntuforums.org/showthread.php?t=2120196)
More tests Flash drives post #5 -  C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2130234](http://ubuntuforums.org/showthread.php?t=2130234)
Brand of flash does seem to make a difference. One user's experience liked 32G Sandisk 
[http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208](http://ubuntuforums.org/showthread.php?t=2120196&p=12577208#post12577208)

My USB3 flash reads about 10% faster even in my old USB2 port. Writes and install are really slow.

   fred@fred-Precise:~$ sudo hdparm -tT /dev/sde
# my 32GB USB3 on USB2 port
/dev/sde:
 Timing cached reads:   7326 MB in  2.00 seconds = 3668.54 MB/sec
 Timing buffered disk reads: 104 MB in  3.02 seconds =  34.44 MB/sec

   fred@fred-Precise:~$ sudo hdparm -tT /dev/sde
# my 16GB USB2 on USB2 port
/dev/sde:
 Timing cached reads:   7192 MB in  2.00 seconds = 3600.81 MB/sec
 Timing buffered disk reads:  94 MB in  3.04 seconds =  30.93 MB/sec

This was not a flash drive but shows with different tests that different file systems are better.
      
 Linux 3.14 File-System HDD Benchmarks
[http://www.phoronix.com/scan.php?page=article&item=linux_314_hdd&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_314_hdd&num=1)

---

### Post by Lockheed on 2014-11-03
Thanks to everyone who answered.

I ended up going for _BTRFS with compress-forece=lzo. _

Also, beceuse I am using Arch linux, I was able to use Profile-sync-daemon and Anything-sync-daemon to put the following folders in ramdisk:
/var/log 
/var/tmp
/home/user/.cache/ - (I have yet to test this one)
and the browser profile for firefox.

**Results: **
It works very well, smooth. Boots to desktop (MATE) in several seconds. Programs load nearly instantly. Very rarely do I get any momentarily lockups. 
This is a much better experience then previous installations I've done on a flash drive.

However, this experience is based on only an hour of tests.

Additionally, I set up Grub2 to chainload to E2B bootloader to easily boot any live ISO I put on sda1 fat32. 

I am content with this setup. The only thing left to do is to setup encryption of the home folder. But problems with that are for another thread.

---

