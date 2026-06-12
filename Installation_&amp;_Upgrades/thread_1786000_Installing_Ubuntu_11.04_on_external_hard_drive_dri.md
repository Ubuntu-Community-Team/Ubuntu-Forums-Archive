---
title: "Installing Ubuntu 11.04 on external hard drive drive..."
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Dave94 on 2011-06-19
Ok - just to warn you guys - I'm a total newbie to all things Linux! - so just bear with me :)

I would like to install Linux Ubuntu 11.04 on an external hard drive - its partitioned and ready for Linux. I've downloaded and burnt the .iso file to a DVD so its all good so far....

First of all... is this possible without messing up my macbook? I don't particularly want to break into my macbook to disconnect the hard drive (I read on a tutorial for a previous version of Ubuntu that I'd have to do that... - does it still apply to 11.04?) - as it voids the warranty (I checked :p ).

The reason I ask this is because I had a friend who partitioned their internal hard drive and installed Ubuntu on it. But after installation was complete they couldn't boot up Windows 7 or Ubuntu... and it resulted in them having to clean install Windows 7... - I don't want to end up in that situation :(

Second... If it is possible to install it without messing up my macbook... - Do I just follow the install instructions but just make sure that where possible I make sure that everything is installed on my external hard drive?...

I really need someone to put my mind at rest that everything will run smoothly and that I'll be able to run Mac OS X as usual but also that I'll be able to boot from my external hard drive to run Ubuntu.

Thanks
Dave

---

### Post by YesWeCan on 2011-06-21
Hi. I'm no expert on macs but the problem that tends to catch people out and trash their Windows is when the Ubuntu installer puts the boot code on the MBR of the wrong disk.

Now, you would expect that if you chose to use an entire disk that the boot code would be put on that disk. That does not always seem to be the case. The installer seems to put it on sda which is usually a persons Windows disk.

So you should be safe as long as you use advanced install to explicitly tell it to put the boot code on the external disk. Eg: /dev/sdc. Not to a partition tho, like sdc1.

---

### Post by tommcd on 2011-06-22
Choose manual partitioning during the install. Select to install Ubuntu to the external drive, which will probably be designated as */dev/sdb* by the partition tool. When you get to the part where you install the grub2 boot loader, select to install it to /dev/sdb. This is not the default, so you will need to select it.
Then to boot Ubuntu, you will need to select to boot from the external hard drive as the first boot device in the Mac book's BIOS. Set the internal hard drive as the second boot device. This way when the external drive is not connected you will be able to boot Apple's closed source operating system normally.
Disclaimer: I have never used anything built by Apple. So this is just the general approach I would take. Doing it this way should not harm anything on your Mac book.

---

