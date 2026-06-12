---
title: "&quot;...desktop would halt and grey out for 10 - 30 seconds...&quot;"
date: 2015-06-26
forum: Installation &amp; Upgrades
---

### Post by Michael_Sinsabaugh on 2015-06-26
I asked for help on making a good bootable thumb drive for Ubuntu ([Run From Thumb Drive]("http://ubuntuforums.org/showthread.php?t=2283885")).  Thank you everybody for your help.  It was easy with the instructions you all provided.  When trying to find the answer for myself I came across a post "[What is persistence]("http://ubuntuforums.org/showthread.php?t=1446347")".  Aside from the topic of the thread post #4 had an interesting observation/question.

> ... I've tried that in the past to a USB stick, and the performace was  horrible; each few minutes the whole desktop would halt and grey out for  10 - 30 seconds, and then become responsive again. My hypothesis: my  USB stick was too slow to be handled as a normal drive...

First my comment about the USB stick being slow.  I thought that most modern day USB sticks/thumb drives were faster than your ordinary hard drive (hence Windows using them to boost speed by using them for swap file).

Anyway (sorry for the long preamble), I've made the boot thumb drive and it seems to work just fine except, every few minutes the whole desktop halts and goes gray for 10 - 30 seconds and then becomes responsive again.  I hate to ask questions that have been asked many times before (and answered) so I spent a lot of time looking for this one and haven't been able to find out what's up.

Any ideas??

---

### Post by dino99 on 2015-06-26
That mean the system is waiting the data flow: either the thumb is too slow, the usb's mobo is too slow or the thumb is pretty full (need at least 15 % free space)

---

### Post by Michael_Sinsabaugh on 2015-06-26
> **dino99 said:**
> That mean the system is waiting the data flow: either the thumb is too slow, the usb's mobo is too slow or the thumb is pretty full (need at least 15 % free space)

I appreciate the reply.  This brings up two questions though 1) I'm not familiar with the term "mobo", 2) when I used the USB installer from [pendrivelinux.com]("http://www.pendrivelinux.com") and just made a bootable installation USB stick, and clicked on "try" when booting from it... I didn't have this problem.  That was using the same USB stick etc.

---

### Post by echotech2 on 2015-06-27
Mobo=Motherboard.

---

### Post by efflandt on 2015-06-28
Flash on a memory stick (or memory card reader) is not the same speed as flash in an SSD. In my experience on USB 2.0 I have never seen a memory stick that was as fast as a portable USB 2.0 hard drive (much less an internal hard drive). So I have no clue why Windows used USB flash memory for virtual memory. What did surprise me when doing some drive speed testing and temporarily installing SSD in an old laptop was that the laptop's SATA1 5400 RPM hard drive was no faster than an external USB 2.0 drive. Although, the SSD (older Intel 80 GB) on SATA1 was about 4 times faster than that 5400 RPM drive, about the same speed as the 7200 RPM 1 TB drive on SATA2 on my desktop. And when I moved the SSD to my desktop on SATA2 it was an additional 2x faster.

Also the OS and programs on live/install iso are on a compressed (squashfs) filesystem on a file and anything loaded from that needs to be uncompressed. So running an iso from USB memory does lag some, although, I do not remember things often getting grayed out. If the memory stick or USB port on an old computer is USB 1.0, that would really be sluggish.

Just a quick test doing **sudo hdparm -Tt**, the "buffered disk reads" in MB/sec were:
22.8 - PNY 4 GB USB 2.0 stick
28.6 - Kingston 8 GB USB 3.0 stick on USB 2.0
32.4 - WD Passport 500GB USB 2.0
250.6 - Old Intel 80 GB SSD SATA2
408.5 - Crucial M550 512 GB mSATA SSD SATA3

---

### Post by Skaperen on 2015-06-28
be sure you plug into the USB _3.0_ slot.  it has the _**[COLOR=#0000cd]BLUE[/COLOR]**_ tab in it.

---

