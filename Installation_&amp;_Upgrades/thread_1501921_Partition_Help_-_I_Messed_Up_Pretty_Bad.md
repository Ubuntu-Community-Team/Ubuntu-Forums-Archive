---
title: "Partition Help - I Messed Up Pretty Bad"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by The Chasm on 2010-06-04
Hello Ubuntu Community,

I'm hoping someone here can be of some use to me and my "problem". Today, I did something stupid and deleted the partition my Ubuntu was running on. (I thought it was a partition I had created that wasn't being used). I restarted the computer, and of course GRUB gave me an error and went to a terminal-like mode that didn't really do anything. IIRC, it was grub recovery> or something like that. From there, I couldn't get to Windows 7, so I went to my desktop and downloaded Kubuntu (which I was planning on switching to, anyway) and put it on a USB drive made with UNetBootin. I was able to boot this up on my laptop and it runs off of the USB just fine. 

Now, though, the installer keeps hanging up right after the keyboard layout part saying "Scanning Disks... 47%". It's been on that for quite some time now, and I pretty much have no idea of what to do from here.

Any help is much appreciated.

Thanks,
**--The Chasm**

---

### Post by The Chasm on 2010-06-05
Bump D:

---

### Post by ankspo71 on 2010-06-05
Hi,
It's hard to say what could be going on but it sounds like it is getting stuck just before the partitioner screen comes up. Do you still have you original Ubuntu cd (or Live USB) to see if that can get past the partitioning stage?

Are you able to check the Kubuntu iso image with an md5sum check? All you need to do is go to a terminal and type:
```
md5sum /path/to/kubuntu-10.04-desktop-i386.iso 
```
then look for a matching md5sum of Kubuntu on the bottom of this page: [http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)

How much memory do you have? Are you able to perform a memory test, either by using your live USB pr installed version of Linux? 

Are you able to burn a cd? If so the cd might work better (because I'm thinking that maybe the partitioner might be getting stuck as it scans the usb drive and I wouldn't know a way around that). Have you tried an alternate cd (or usb if it works on usb)? 

If none of this helps, consider it another bump to your original message. Someone's bound to know.

---

