---
title: "Installation problem Lucid Lynx"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by John Petley on 2010-06-07
Please can someone help. I have a bit of a saga here.

Some time ago I loaded 8.04 (dual boot with windows XP) for the first time and happily used Ubuntu. I then upgraded to 9.04 and got problems with disc space. This turned out to be due to the CPU overheating and the fact being recorded repeatedly in log files. I dealt with the CPU overheating problem and have not seen this message again but 9.04 kept hanging during boot up. I could get different responses by pressing keys (arrows, space bar or return) when nothing was happening but could not get the thing going. So I gave up and went back to XP. I decided to try again with 10.04 from a magazine DVD and this would not work, even to load from the DVD. Repeated attempts suggested that the DVD reader was not reading properly as I seemed to get to different places along the boot up each time. Knowing that the optical reader works fine for CDs (I have recently completely reinstalled XP and a lot of windows programs without a hitch), I downloaded 10.04 to a CD and tried again.
first off it hung again but I noticed that pressing the down arrow revealed a text message about a userid being missing (it was marked step 430, I think) but eventually it got past this and loaded 10.04 from the CD. Hooray! I then tried loading Ubuntu onto my system. All went well up to the partition  step. I wanted to change from the following partitions:
sda1 - XP 53.7 Gbytes
sda? - Ubuntu 9.04 64.1 Gbytes
sda? - swap 2.3 Gbytes

to the following (which I did using the slider in the Prepare disk space option):
sda1 - XP 53.7 Gbytes
sda5 - Ubuntu 9.04 14.1 Gbytes
sda? - Ubuntu 10.04 50.0 Gbytes
sda? - swap 2.3 Gbytes

All proceeded fine with the Please wait ... Resizing partition until it got to 50% where it has stuck. The whole system is locked down to the mouse pointer. CTRL/ALT/DEL gets no response. It has been like this for some hours now and there is no indication of disk activity.

I am not a techy person but know enough that switching off during a repartition could be unwise so please can you advise how to proceed.

My system details are:
Sony laptop PCG-GRT786M
2.66 G hertz pentium 4
120 Gbyte hard drive (not original)

Thank you for reading through all  this. I look forward to help

Kind regards

John

---

### Post by oldfred on 2010-06-07
The normal auto installs assume you have a windows to shrink an it will make space for the new install. Or you have unallocated space to install into. With the old install it may be having trouble auto moving everything around.

Do you really want to keep the old install? If so I think you have to do manual partitioning and a manual install. I also partition first and make sure windows still boots ok, then do manual install. You can do it all as one but then if windows has issues you do not know why.

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Different versions of windows or Ubuntu do not have significant differences. Win7 should use internal tools to resize win partition, XP you can use gparted. For Ubuntu the newer versions use grub2.

Dual Boot win/10.04
[http://members.iinet.net.au/~herman546/p23.html](http://members.iinet.net.au/~herman546/p23.html)
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

