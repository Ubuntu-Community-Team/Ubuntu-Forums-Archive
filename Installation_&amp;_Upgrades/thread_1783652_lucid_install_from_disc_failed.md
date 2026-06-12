---
title: "lucid install from disc failed"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by bullfrog55 on 2011-06-16
I want to reinstall lucid for various reasons, so I downloaded the file, burnt it to cd and then booted with the cd in. An ubuntu screen started then went to a black screen with the message:
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: input/output error
Can not mount /dev/loop0(1cdrom/casper/filesystem.squashfs) on //filesystem.squashfs

then no further progress.

I reburnt the disc (4 times) making sure that the fies were executable but still no good. 
How do I do this?

:(

---

### Post by tommcd on 2011-06-16
Be sure to run the option to check the CD for defects to rule out a bad CD. When you get to the Ubuntu boot screen you should be able to hit any key to see the menu where you can select the option to check the CD for defects.

---

### Post by sidzen on 2011-06-16
Burn at no more than 8X
Also, check the md5sum

---

### Post by mörgæs on 2011-06-16
The error reported is often related to booting from CD in general. Try booting from USB created with Unetbootin rather than burning more CD's. 

Also, there is no indication that the ISO is bad. You can of course do the MD5 test, but it is not likely that you will find errors here.

---

### Post by bullfrog55 on 2011-06-18
I tried unetbootin but found no way of booting from the usb stick. The only options in the bios were usb-hdd, floppy,cd, and another one which was not a usb stick. I also tried downloading the iso using unetbootin but twice the download stopped about 3 quarters of the way through - annoying. 
The usb has the files to boot from but I find no way of doing it.

---

### Post by mörgæs on 2011-06-18
Then your computer is too old for booting from BIOS. You could either try upgrading the BIOS or this approach:

[http://andyduffell.com/techblog/?tag=perfectminimal](http://andyduffell.com/techblog/?tag=perfectminimal)

---

### Post by bullfrog55 on 2011-09-20
Finally figured this thing out. I tried burning another cd (cd RW) using another computer and had exactly the same problem. I ran out of CDs and so used a DVD R. It worked fine. I think the problem lay with the fact that it was a CD RW. I don't know about a CD R but I certainly won't use a CD RW again when I want to make an install dsc. 
Incidentally, I went to Natty this time as the laptop I decided to use was a bit newer than the old desktop I was trying to wring every last drop of use from. 

Thanks for all the help. I reckon we can call this one solved.

---

### Post by mörgæs on 2011-09-20
Good, then it would be great if you mark the thread 'solved' using 'thread tools' (I have done it for you this time).

---

### Post by shlagbaum on 2011-09-24
> **mörgæs said:**
> Good, then it would be great if you mark the thread 'solved' using 'thread tools' (I have done it for you this time).

I'm afraid you marked it "solved" too soon. I have the same problem. I wanted to replace win xp with ubuntu on my rather old compaq (amd64). I tried different versions on different cd's and all of them were CD R. Basically there were two outcomes: either the one indicated at the beginning of the thread or installation just hangs forever. Installation from a USB stick is not an option - too old bios. Any other ideas? Please advise. Thanks

---

### Post by mörgæs on 2011-09-25
Welcome to the fora.

It is solved from original poster's view, but you are welcome to post. 
First, please give a complete hardware description. 

Which versions have you tried?
Could the CD's you made boot on another computer?

---

### Post by tommcd on 2011-09-25
> **shlagbaum said:**
> I'm afraid you marked it "solved" too soon. I have the same problem. ...
To give us your hardware specs, boot up the Ubuntu live CD, open a terminal, and run this command:
```
lspci -k
```
This will tell us your hardware (lspci) and the kernel module ( -k) in use for each hardware device.

Also please check the CD for defects as I discussed in post #2 in this thread.
Which Ubuntu versions are you trying to install? You should be using either the current version 11.04, or the most recent long term support (LTS) version which is 10.04.

And welcome to the Ubuntu forums!

---

