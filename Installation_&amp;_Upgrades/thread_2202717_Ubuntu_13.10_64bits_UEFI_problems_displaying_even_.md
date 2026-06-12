---
title: "Ubuntu 13.10 64bits UEFI problems displaying even console [view image]"
date: 2014-01-30
forum: Installation &amp; Upgrades
---

### Post by realavaloro on 2014-01-30
Hi,

I am having issues to get Ubuntu installed on my Dell XPS 13'' with the following specs:
-UEFI on SSD drive 
-Windows 8.1 OEM installed (I just installed it myself and I left unallocated space on the SSD drive where I was planning to install Ubuntu to coexist)
-Intel i5-4200U processor with Intel® HD Graphics 4400
-In Windows I've got a high resolution 1920x1080 (FHD)

I was able to place the Ubuntu 13.10 64bits into a USB pendrive and boot it as UEFI (I used Lili USB creator after formating the USB pendrive as FAT32)
When I boot the system with the USB pendrive I get to the main Ubuntu options screen.
I am having exactly the same problem if I try to install Ubuntu directly or if I try Ubuntu without installing it (Live CD)

The PROBLEM is the screen. I can see the logo with horizontal lines, as if there was some kind of problem with my graphic card. Then the main screen to choose language exactly with the same shaky shape and repeated image, and when I try the LiveCD same problem occurs.
Even if I switch to CONSOLE (no graphic mode!) I see the comman line shaky and with horizontal lines.. so that's weird.

See the image to have an idea:
[IMG]http://oi61.tinypic.com/a2tyxt.jpg[/IMG]

I have not tried with Ubuntu 12.04 as it won't boot (It brings me to this Busy Box prompt and I assume it's due to incompatibility with UEFI)

Could anybody advise on what to try? Much appreciated!!

PD: When I installed Ubuntu 13.10 in a Virtual Box machine everything was ok. I even installed the host tools to be able to see Ubuntu with the highest resolution supported 1920x1080 and everything was good.

---

### Post by oldfred on 2014-01-30
Same issue. See screen shot in post #7.
[http://ubuntuforums.org/showthread.php?t=2198946](http://ubuntuforums.org/showthread.php?t=2198946)

While not specifically suggesting 14.04, one user said that worked.

Dell issues are similar across models, some useful comments on i915 driver.
       Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)

---

### Post by realavaloro on 2014-01-31
Thank you for your reply.
Glad to see there was already a post regarding the same, sad to see there is no good solution. 

I will give it a try with ubuntu 14.04 see what happens before giving up and I'll post my experience on the other thread you told me.

Cheers

---

### Post by Byeong_Gon_Lee on 2014-09-14
I have same graphics card and similar problem 
look at this : [http://www.youtube.com/watch?v=BPRci098U7c](http://www.youtube.com/watch?v=BPRci098U7c)
For me the only workaround is disable KMS and it turns off graphics acceleration 
to disable KMS you should add "i915.modeset=0" to
"GRUB_CMDLINE_LINUX_DEFAULT="

---

