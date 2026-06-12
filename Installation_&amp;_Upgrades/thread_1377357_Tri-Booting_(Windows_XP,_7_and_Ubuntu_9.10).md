---
title: "Tri-Booting (Windows XP, 7 and Ubuntu 9.10)"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by jackhe22 on 2010-01-10
Hello people of Linux!,

I've just downloaded, burned and verified my new Ubuntu 9.10 disc, for installing on my trusty PC, which is currently Dual-Booting between Windows 7 RC and Windows XP Home. I have run Ubuntu in the past, but I always had Screen Resolution problems, and am willing to give it another go.
This post is here because I'm not sure if there is anything I need to be aware of before I start. 
If its any help, Windows 7 RC was installed after XP, so the 7 boot menu is there,
The hard drive is partitioned.  The 7 Partition has 30 GB and the XP the rest. To do it, I have been using Paragon Partition Manager 8, which I got free in a magazine. Its running inside XP.

If this goes smoothly, and I get that resolution error fixed, I may consider moving to Ubuntu completely!

Thanks for your help!,
jackhe22 ;)

---

### Post by wirate on 2010-01-10
Karmic has resolution problems but fixing them is easy. Jaunty doesnt. Apparently you have only two partitions so which one are you going to use for Ubuntu? Or are you going to make a new one?

---

### Post by jackhe22 on 2010-01-10
> **wirate said:**
> Karmic has resolution problems but fixing them is easy. Jaunty doesnt. Apparently you have only two partitions so which one are you going to use for Ubuntu? Or are you going to make a new one?
Hello Wirate, thanks for the quick reply.
I intend to boot into XP and resize XP's partition. Once I have done that I will create a new partition for Ubuntu. Approx. 40GB or so? in the ext3 File system. 
Also, thanks for the reply about resolution problems. Every time I ever had Ubuntu (since 8.04 LTS) it would always load up in 800x600, and the native monitor res is actually 1280x1024. In the Resolution Program, 800x600 was the max I could change. I tried even the complicated stuff like terminal commands and xorg? (I can't remember most of the names.... It really has been that long) with no success. Thats when I binned it, and got rid of Ubuntu. 800x600 is too small a working space and appears badly on my screen.

Thanks for the reply,
jackhe22
:-)

---

### Post by darkod on 2010-01-10
Resolution limitation would usually be related to video card driver, and not the monitor itself. The same thing occurs under windows, unless the driver for the card is correct, it can work only on lower resolutions.
When shrinking the XP partition to create unpartitioned space for ubuntu remember this: it doesn't matter how you shrink the XP partition, there are few ways to do it, but DO NOT proceed with ubuntu install right away. First boot XP few times to make sure it's happy with the shrink. It will need to run few disk checks.

Because of the above I never recommend using the ubuntu installer to shrink XP partition as part of the install process because the process will continue without giving XP chance to make the disk checks.
You can shrink it by booting with ubuntu cd, Try Ubuntu option, and using Gparted from it. Another option is third party software because XP does not have the option to shrink partitions in it (like Vista and 7).

---

### Post by jackhe22 on 2010-01-10
> **darkod said:**
> Resolution limitation would usually be related to video card driver, and not the monitor itself. The same thing occurs under windows, unless the driver for the card is correct, it can work only on lower resolutions.
When shrinking the XP partition to create unpartitioned space for ubuntu remember this: it doesn't matter how you shrink the XP partition, there are few ways to do it, but DO NOT proceed with ubuntu install right away. First boot XP few times to make sure it's happy with the shrink. It will need to run few disk checks.

Because of the above I never recommend using the ubuntu installer to shrink XP partition as part of the install process because the process will continue without giving XP chance to make the disk checks.
You can shrink it by booting with ubuntu cd, Try Ubuntu option, and using Gparted from it. Another option is third party software because XP does not have the option to shrink partitions in it (like Vista and 7).
Thanks for the reply, Darko.
The software I use for partitioning (Paragon Partition Manager 8 ) can shrink within Windows. It reboots and does it within a pre-windows state. I know all about the disk checks -believe me! When I was partitioning for Windows 7, I thought I had killed my HD when it came up with Disk Checks on XP!

About the resolution, when I used to install the restricted drivers, it enabled Compiz Fusion, but made the res worse. 800x600 to 640x480 or 320x240. The funny thing, is that when I first installed Ubuntu, the res was fine. I had it all customized with Compiz, drivers and Flash Player. (took a while to fix, Flash Player!) and then one day, I booted it up, and it all went wrong.

Thanks for the help!.
jackhe22

---

### Post by jackhe22 on 2010-01-10
Bump :(

---

### Post by darkod on 2010-01-10
I have no clue about the resolution problem but rereading your posts it seems you are asking this question in advance. Why not install 9.10 and see whether a problem will exist at all?
Since you are aware about the XP shrinking issues, do the shrinking, install 9.10 in the created free space, and see how it goes.
Also, this is the Installation subsection of the forum and you might get more expertise for video issues in other subsections.

Another thought, did you try booting with the ubuntu cd and Try Ubuntu option to see how will it run from the cd? You will probably see what resolution you can use like that.

---

### Post by jackhe22 on 2010-01-10
Thanks again Darko, I will try now on Live CD before doing any partitioning. Regarding the resolution problem, I will move it to the video section if the problem still exists. If its any help, I have a similar res problem in XP and 7 too! It thinks the max is 2040x2000! I think its an error with EDID signals and my Graphics Card.

---

### Post by jackhe22 on 2010-01-10
URGENT:

Okay, ive tried booting up in Live. But this is worse than ever. My monitor went off, came back on and said in big letters:
MODE NOT SUPPORTED.
H: 93.0kHZ V: 58.5hz.

Now I don't know what to do! Urgent Help!

---

### Post by jackhe22 on 2010-01-10
Ive had to Hard Power Down.

I tried everything, to no prevail.
This is worse than ever. I would really like to run Ubuntu, but this problem just wont leave me alone. No matter what distro it is.

---

### Post by darkod on 2010-01-10
> **jackhe22 said:**
> URGENT:

Okay, ive tried booting up in Live. But this is worse than ever. My monitor went off, came back on and said in big letters:
MODE NOT SUPPORTED.
H: 93.0kHZ V: 58.5hz.

Now I don't know what to do! Urgent Help!

The 93kHz H freq sounds too high. I don't think even new monitor models could support it. I have no clue though why is it asking the monitor to work at 93kHz. Sorry.

---

### Post by jackhe22 on 2010-01-10
Bump
:'(

---

### Post by jackhe22 on 2010-01-10
Bump

---

### Post by jackhe22 on 2010-01-10
I'm sorry, but this really is the last time. I'm not using Linux or any other Linux based system again. They just either don't work or take months of your life to try and fix. I think I will stick with my Mac for now. Thanks anyway, Ubuntu Community, but Ubuntu is not for me.

---

### Post by jackhe22 on 2010-01-10
Thanks anyway Darko..

---

### Post by wirate on 2010-01-12
If this thread still matters to you ;),
try this
(sample)
```
cvt 1024 768 75
```
the output is like
```
# 1024x768 74.90 Hz (CVT 0.79M3) hsync: 60.29 kHz; pclk: 82.00 MHz
Modeline "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync

```
now (copy and paste the thing after "Modeline")
```
xrandr --newmode "1024x768_75.00"   82.00  1024 1088 1192 1360  768 771 775 805 -hsync +vsync
```
now (VGA1 or whatever it is you can find by typing just xrandr)
```
xrandr --addmode VGA1  "1024x768_75.00"
```
Hope this helps

---

