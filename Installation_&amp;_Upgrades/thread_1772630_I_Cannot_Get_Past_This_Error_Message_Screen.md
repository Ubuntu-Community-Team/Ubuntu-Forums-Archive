---
title: "I Cannot Get Past This Error Message Screen"
date: 2011-05-31
forum: Installation &amp; Upgrades
---

### Post by Dan David on 2011-05-31
First off, I don't know if anyone can help me on this but I could use all the help I can get. I will be as much info as possible to give you the best understanding of my problem.

Ok, let me start from the beginning. 

   I am 20 years old. I have a Gateway M-7356u laptop with Windows Vista Home Premium pre-installed on it. Something happened (a virus?) and I could not start it up anymore. The only thing that I can do is load the BIOS from this point on. I figured I would then wipe the hard drive completely and start over with WipeDrive 6. Weeks later, I found Ubuntu 11.04 OS on this computer and wanted to give it a try. So I do. I downloaded it using this computer, got a blank disc, burned the .ISO image onto it and put the disc in my laptop. I start it up. Go to the BIOS to make the CD ROM drive run first. I see Ubuntu logo and get excited. Then, this screen pops up and that's all I know from here. 
This is where I am stuck.

"BusyBox v1.17.1 (Ubuntu 1:1.17.1-10ubuntu1)built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Input/output error 
Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystems.squashfs 
udevd[74]: worker [195] failed while handling '/devices/virtual/block/loop0' "


   There is no UI, just this screen, which I am guessing is in GRUB 2. This is just before the installation so don't tell me to go to the Dash > Places and select this drive. I don't have the OS yet so this doesn't help me.

   I consider myself highly intelligent when it comes to computers and electronics and fixing things but I can't seem to figure this out and I've tried everything I could think of. I looked through many forums and support pages, how-tos, you name it. I don't know if anyone can help me but I appreciate anything you can give me. I am near giving up. This is my last option. If this doesn't work, I will stop trying to find a way. At least I can say I have given it my all.

---

### Post by NoBugs! on 2011-05-31
If you checked the cd and it has no errors, it may be a hardware failure. Have you booted from usb?

---

### Post by Dan David on 2011-05-31
No, it has USB ports but I don't have anything to boot it from there with.

---

### Post by drs305 on 2011-05-31
Dan David,

Welcome the Ubuntu Forums!

There should be an option to check the CD for defects as one of the boot options if you get to the CD menu. 

If you see the two icons in the center bottom of the screen and the CD has checked OK, try pressing F6. You may need to boot with some special options until you can install the drivers. One example is 'nomodeset'.

Here is a link that explains how to access these special options.
[https://help.ubuntu.com/community/LiveCDBootOptions]("https://help.ubuntu.com/community/LiveCDBootOptions")

---

### Post by Dan David on 2011-05-31
Ok, here's an update on what I've been doing. I've got to the CD menu. I tried all the options and pressed F6 and tried each one of those. I'm still getting the error message screen but sometimes with the last line missing, and then there is an occasional bunch of stuff that I am not going to type because it's too much and fast to read it all and at the bottom it says something did something "Reboot required", but I can't do it or anything without taking out the battery to shut it off and start all over again. I went to the Help screen after pressing F1 and then F4. It says:

"There is no dedicated rescue mode on this disc. However, since the disc provides a complete user enviornment, it is possible to use the command-line and/or graphical tools provided to rescue a broken system, and to use a web browser to search for help." 

I don't know how to get to the web browser or use the tools. Then, I tried the "Boot From Hard Drive" option for the heck of it and that just kept going endlessly. So, I didn't get much farther from where I got stuck before. At least I now know for certain there is nothing wrong with the disc. Hope this helps.

---

### Post by Dan David on 2011-06-01
I am now trying the Ultimate Boot CD to see if this fixes my problem. I will let you know if it worked or not.

---

### Post by Dan David on 2011-06-03
Well, I can't figure it out. I've tried everything that I can possibly think of. I give up. Thanks for trying to help though.

---

