---
title: "Ubuntu won't start after the orange bar..."
date: 2008-06-13
forum: Installation &amp; Upgrades
---

### Post by jcroot on 2008-06-13
Hi guys!

I'm decided to try Ubuntu 8.04 and for some reason I'm having a problem with the installation. I have a desktop PC which is 1.00 Ghz and it has about 768 Mbs of ram. This PC also has a DVD/CD room and basically I build this PC my self. I currently have Windows XP installed in this PC and I would like to change it for Ubuntu 8.04.

My bios is setup to boot from the DVD/CD room first and I'm able to boot from the CD, when I boot from the ubuntu CD I see some options I just choose the second option which is "install ubuntu etc". After that I see the orange bar loading something and after a few minutes I only see a black screen, not matter how long I wait I see the black screen all the time after the orange bar.

I changed my DVD/CD room because I believed this was the problem but is not... at first it worked, I was able to see the ubuntu windows after the orange bar finished loading (I didn't instal ubuntu at the time thought) but right now I'm not able to see anything just the black screen.

Does any body know what could this problem be?

---

### Post by overdrank on 2008-06-14
> **jcroot said:**
> Hi guys!

I'm decided to try Ubuntu 8.04 and for some reason I'm having a problem with the installation. I have a desktop PC which is 1.00 Ghz and it has about 768 Mbs of ram. This PC also has a DVD/CD room and basically I build this PC my self. I currently have Windows XP installed in this PC and I would like to change it for Ubuntu 8.04.

My bios is setup to boot from the DVD/CD room first and I'm able to boot from the CD, when I boot from the ubuntu CD I see some options I just choose the second option which is "install ubuntu etc". After that I see the orange bar loading something and after a few minutes I only see a black screen, not matter how long I wait I see the black screen all the time after the orange bar.

I changed my DVD/CD room because I believed this was the problem but is not... at first it worked, I was able to see the ubuntu windows after the orange bar finished loading (I didn't instal ubuntu at the time thought) but right now I'm not able to see anything just the black screen.

Does any body know what could this problem be?

HI have you checked the cd for errors and also checked the MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by jcroot on 2008-06-14
> **overdrank said:**
> HI have you checked the cd for errors and also checked the MD5SUM
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Hi!

I checked the CD for errors and it doesn't contain any error. I forgot to mention that the CD is the original that Ubuntu send me.

---

### Post by avtolle on 2008-06-14
Before recommending you d/l the alternate install CD iso, a question or two:

1) Do you have SATA drives?

2) What is your graphics card?

---

### Post by jcroot on 2008-06-14
> **avtolle said:**
> Before recommending you d/l the alternate install CD iso, a question or two:

1) Do you have SATA drives?

2) What is your graphics card?

No, I don't have any SATA drives... I'm currently using PATA Drives.

My graphics card is:

Intel(R) 82845G Graphics controller.

---

### Post by VMC on 2008-06-14
Have you tried to just let the ubuntu cd just bootup to a livecd ubuntu system? If you can there is a install icon on the desktop. Try that.

---

### Post by javeh on 2008-06-14
Hi!

Im having a similar problem jcroot, the installer doesnt load after the orange bar - it just goes to a command prompt looking screen "busybox v.1.1.3". Im using 2 sata and 2 ide hard drives and my gfx is ati radeon x800.

im just starting out with linux so i apologise for the simplicity of my post.

cheers

---

### Post by Habbit on 2008-06-14
If the problem is with your video card, you could try installing through the Alternate CD (with the text installer)

---

### Post by avtolle on 2008-06-14
> **javeh said:**
> Hi!

Im having a similar problem jcroot, the installer doesnt load after the orange bar - it just goes to a command prompt looking screen "busybox v.1.1.3". Im using 2 sata and 2 ide hard drives and my gfx is ati radeon x800.

im just starting out with linux so i apologise for the simplicity of my post.

cheers
Try this: at bootup, hit F6; at the end of the boot line that appears, add by typing, all-generic-ide and see if that helps you at all. I'm no expert on SATA drives, but recall reading various threads that this boot parameter has helped some.

---

### Post by javeh on 2008-06-14
> **avtolle said:**
> Try this: at bootup, hit F6; at the end of the boot line that appears, add by typing, all-generic-ide and see if that helps you at all. I'm no expert on SATA drives, but recall reading various threads that this boot parameter has helped some.

thanks, im just reading the thread about it now, it seems a bit intimidating that different users are finding different solutions to the problem, but i'll try that before i go any further. thanks again

---

### Post by upchucky on 2008-06-14
it's been a while, since i had to do this, but i remember having the same problem, I had to boot into command line mode, (init3) i think, then i had to edit the xorg conf to use vesa driver, init5 then redo later with proper settings for my vid card.

search the site for boot options and vid card settings, vesa settings and init settings to find the right files to edit.

i found vim an easy editor to use, but there are many others that work just fine.

---

### Post by javeh on 2008-06-15
thanks for the help guys, i tried the all_generic_ide trick and it installed fine!

---

### Post by jcroot on 2008-06-15
> **VMC said:**
> Have you tried to just let the ubuntu cd just bootup to a livecd ubuntu system? If you can there is a install icon on the desktop. Try that.

I tried this also and is not working, same problem...

---

### Post by jcroot on 2008-06-15
> **javeh said:**
> Hi!

Im having a similar problem jcroot, the installer doesnt load after the orange bar - it just goes to a command prompt looking screen "busybox v.1.1.3". Im using 2 sata and 2 ide hard drives and my gfx is ati radeon x800.

im just starting out with linux so i apologise for the simplicity of my post.

cheers

No worries!

Thanks for your comment and for sharing it.

Cheers

---

### Post by jcroot on 2008-06-15
> **avtolle said:**
> Try this: at bootup, hit F6; at the end of the boot line that appears, add by typing, all-generic-ide and see if that helps you at all. I'm no expert on SATA drives, but recall reading various threads that this boot parameter has helped some.

I really don't know if this will fix my problem since I'm not having the same exact problem as "javeh".

What else can I try guys?

---

### Post by jcroot on 2008-06-15
Well I finally installed Ubuntu 8.04 

What I did is this (just in case somebody else have the same exact problem):

I boot from the CD then I hit F4 (to choose the mode) and I choose "safe graphic mode" or something similar (I can't remember". With this mode I was able to install Ubuntu.

The only problem that I'm having right now is my PC resolution. I can't change the resolution to 1024x768. My current resolution is: 640x480

I went to System->preferences-> and screen resolution, I can't see any other option but 640x480

I followed this thread:

[http://ubuntuforums.org/showthread.php?t=829691&highlight=can%27t+change+screen+resolution](http://ubuntuforums.org/showthread.php?t=829691&highlight=can%27t+change+screen+resolution)

But it the solution didnt' work for me...

I believe I maybe got stuck or confuse in this:

```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=800
```

---

