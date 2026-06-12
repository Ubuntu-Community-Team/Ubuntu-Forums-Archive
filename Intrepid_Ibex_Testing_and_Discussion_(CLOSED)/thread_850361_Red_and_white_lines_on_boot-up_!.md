---
title: "Red and white lines on boot-up !"
date: 2008-07-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by chives on 2008-07-05
Have been running 8.10 for a week. Very responsive to my commands and an OS that is extremely easy to use and maintain.

  Slight issue with the sound, but no matter. However, I am now getting  " red and white lines / blocks " on boot-up prior to log-in. Also occurs when shutting down. 

  I cannot find any reference to this anomaly on the forum. Is this unique to my machine ?  MSI MEGA mPC 800K. 

On-Board VGA
	

. K8M800 Integrated UniChrome 2 Graphics
. On-Board VGA memory: Shared

[http://global.msi.com.tw/index.php?func=proddesc&prod_no=8&maincat_no=134&cat2_no=&cat3_no=](http://global.msi.com.tw/index.php?func=proddesc&prod_no=8&maincat_no=134&cat2_no=&cat3_no=)


chives.

---

### Post by damis648 on 2008-07-05
If they appear for less than two seconds, this is not an issue as it is a bug with the video drivers. There is not much you can do, except install the official drivers for you video card if you have not already done so. Go to System>Administration>Hardware Drivers and check the box next to your graphics card and reboot. If they appear for an extended period of time, you have a bigger issue on your hands. As far as the audio issue, what is it? Maybe we can help?

---

### Post by autocrosser on 2008-07-05
It's a issue with some systems/video cards & Usplash--I have at times the red/white & green/white--nothing but black---text only & sometimes a "normal" boot with the splash--sometimes splash with coloured text below. Happens without any good reason.

I remember this was happening when Usplash first started (Edgy) & just wait it out--I'm running a Gigabyte P35/Intel Core Duo & Nvidia 8600 GT-OC (known to have "issues")...I've got a bug started at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

You might add to the bug to keep it alive--I know that it's a Usplash problem....

---

### Post by Nullack on 2008-07-05
Interestingly I dont use splash and I cant set a higher res grub boot anymore since kernel -3

---

### Post by autocrosser on 2008-07-05
So are you doing "text only"?--Grub is only in effect for kernel selection--after the kernel is selected, grub hands off to whatever comes right after.

You could ask for a "vga=xxx" line in your menu.lst. I at times have over-ridden the usplash.conf (I do use Usplash) with a specific setting. I don't remember right now how to define the vga=  there is a 3 digit definer for various resolutions....asomething like 791 thru 795 or so....seems to me that 791=600x480. Someone could jump in here with the numbers ;)

---

### Post by Nullack on 2008-07-05
Thats my point - using vga= values that used to work before -3 no longer does. In fact any value other than default doesnt seem to.

---

### Post by autocrosser on 2008-07-05
Don't know what could have been changed in the .3 kernel, but my guess is that is where it is---sounds like a bug report is in order......

---

### Post by stari4ek on 2008-07-07
I have the same bug.
As I understand - this happens, cause 2.6.26-3 switched from vesafb to uvesafb, which doesn't work really (maybe only with nvidia cards).

temporary fix (i don't use splash):
in grub press 'e'. find line with "vga=XXX" change it to "vga=ask"
press "enter" press "b"

kernel will ask you to press Enter and show you list of available modes. Choose one of VGA mode (VESA modes don't work).
OK. boot!
when you find good mode for you - you can change /boot/grub/menu.lst permanently.

I posted bug to launchpad:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/246269)

---

### Post by midtown on 2008-08-20
> **chives said:**
> I cannot find any reference to this anomaly on the forum.

That's because it's a bug; you should look for bug references on the bug tracker :) [https://bugs.launchpad.net/ubuntu/intrepid/+source/usplash/+bug/243682](https://bugs.launchpad.net/ubuntu/intrepid/+source/usplash/+bug/243682)

> **chives said:**
> Is this unique to my machine ? MSI MEGA mPC 800K.

It does not appear so!

---

### Post by stmiller on 2008-08-20
There is already a bug report for this, as mentioned above:

[https://bugs.launchpad.net/ubuntu/intrepid/+source/usplash/+bug/243682](https://bugs.launchpad.net/ubuntu/intrepid/+source/usplash/+bug/243682)

You can remove the word 'splash' from your /boot/grub/menu.lst line to just have a standard text startup screen in the meantime.

---

### Post by Trespasser on 2008-08-20
I'm having the same issue. It has been that way since day one with Intrepid Ibex. Running an ATI Radeon 9600 Pro AGP video card.

---

### Post by Gina on 2008-08-21
Yes, same here on this machine (P4) with ATI Radeon X640XL PCI-E graphics card and the fglrx driver.  It refuses to work at all with the proprietry driver.

---

### Post by aamukahvi on 2008-08-21
> **Gina said:**
> Yes, same here on this machine (P4) with ATI Radeon X640XL PCI-E graphics card and the fglrx driver.  It refuses to work at all with the proprietry driver.
the fglrx driver doesn't support X.org 7.4.

---

