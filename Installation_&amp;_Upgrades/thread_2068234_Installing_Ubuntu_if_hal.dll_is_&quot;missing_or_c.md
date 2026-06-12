---
title: "Installing Ubuntu if hal.dll is &quot;missing or corrupt&quot;"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by Andyj2008 on 2012-10-08
Good evening,
I am brand new on here but have been using Ubuntu (as a partition on my personal and work computers) for quite a few years. I would like to pick everyone's brains about installing Ubuntu on an old laptop, eliminating Windows altogether.

The laptop in question died on me about 3 years ago with the error "windows could not start because the following file is missing or corrupt: windows system32 hal.dll"

I wanted to buy a new laptop anyway so that was excellent encouragement. My question is this, can I install Ubuntu on the "dead£ laptop without reinstalling the missing/corrupt hal.dll file?

I have had a bit of a play around and can access all of the BIOs and boot menus and can even get a pen drive to light up (on which I have saved the ubuntu.iso files) but it doesn't seem to want to do anything.

Does anybody have any idea how I could get around this? Sorry if this is a stupid question, or if it has been asked before I cant get anywhere with it at the moment.

Many thanks in advance.

---

### Post by Old_Grey_Wolf on 2012-10-08
Linux doesn't care if the .dll file is there or not.

You can't just copy the iso to a USB and install it.

Here are some instructions for creating an install USB using Windows. [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

Here are some instructions for creating an install USB using Ubuntu. [http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by vandorjw on 2012-10-08
If you ae unable to correctly burn ISO images to disk, or have difficulty with booting from USB, (Not all computers can boot from USB) you can purchase an installation CD from the Canonical Store:

[http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17)

It is as simple as putting the disk into your machine and following the step by step instructions.

Best of luck.

---

### Post by efflandt on 2012-10-08
Were any partitions changed on the computer, because when I had that issue on a computer that I had use PING on (partition image is not ghost) it changed boot.ini to point to a different partition before it made the partition images, thinking that you would not reinstall a Dell recovery partition, but it forgot to change boot.ini back to what it was.  So with boot.ini in the WinXP partition pointing at the wrong partition, I got the missing hal.dll error, until I somehow figured that out and corrected boot.ini.

But if you are going to install Ubuntu from CD (or bootable USB), don't even worry about that bacause it you can chose to use the entire drive and it will totally reformat it.  All that matters is whether the drive was developing bad sectors, which is a bad sign that the drive is failing.  Normally a drive transparently remaps bad sectors to reserved good sectors, and if you start seeing bad sectors because it ran out of spares, it can only get worse.

---

### Post by Andyj2008 on 2012-10-09
Hi, 
Thankyou for your replies, I have now set up the USB correctly but still no joy. 

I am now getting as far as being able to choose to install or run Ubuntu but when I do I get the error: timeout: killing /sbin/blkid etc etc!

I have a feeling this is terminal!

---

