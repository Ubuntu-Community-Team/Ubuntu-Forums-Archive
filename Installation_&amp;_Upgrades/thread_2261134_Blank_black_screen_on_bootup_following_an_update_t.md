---
title: "Blank black screen on bootup following an update today (16th Jan 2015)"
date: 2015-01-16
forum: Installation &amp; Upgrades
---

### Post by Malcolm_Brown on 2015-01-16
I have an old Toshiba Satellite Pro laptop which has Intel(R) 945 Express graphics.  After updating my Ubuntu v. 14 today (16th January 2015) using Synaptics Package Manager, I am now unable to use Ubuntu at all.  On bootup I get a black blank screen.  I think that Ubuntu has probably booted up but am unable to see any information.  I strongly suspect that the update has overwritten the graphics driver with something which is unsuitable.  I had this same problem after an update a year or so ago.  I had to do a complete fresh install of Ubuntu and all the software packages I had used.  This took ages.  Is there an easier 'fix'?  Please inform the update team of the problem.  Thanks.

---

### Post by MAFoElffen on 2015-01-16
Can you boot it from a LiveCD and post your var/log/apt/history.log and var/log/Xorg.0.log files. When you post them, go to "Go Advanced" ...> Use [ code ] tags by using the "#" icon at the advanced post menu toolbar > then copy paste those files inside those tags.

---

### Post by Malcolm_Brown on 2015-01-17
I have attached the history anf Xorg files as you suggested.  I had to split the Xorg file into two parts to fit with the upload limit.

Thanks for your help.  Hope the file contents are of use.

---

### Post by steven-misshula on 2015-01-17
I think i'm having the same godforsaken problem....
any and all help is welcome...just started last night....

my issue is that it won't boot and i get the GNU GRUB version 2.02~beta2-9 ubuntu1 screen

as featured in this:

[http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/](http://www.howtogeek.com/196740/how-to-fix-an-ubuntu-system-when-it-wont-boot/) 

but the available recoveries don't work...

---

### Post by MAFoElffen on 2015-01-18
Looking at your logs right now... (brb)

Steve- You look like you are having a different problem if yours is like that, please start a new thread for "yours" to get help on it, describing what is going on with yours...

---

### Post by MAFoElffen on 2015-01-18
I see that Xorg says your driver loaded, and said it had no errors... but you are getting a black screen. 
So in your upgrade was linux-image-generic:i386 (3.13.0.43.50, 3.13.0.44.51) and libc6:i386 (2.19-0ubuntu6.4, 2.19-0ubuntu6.5)... You didn't have an XServer update, so still running the same xserver-xorg-video-intel 2:2.99.910-0ubuntu1.3 driver that was before that update.

Could you post your sources.list... or check it yourself and see if your have proposed selected for some reason... I see that kernel update as proposed but not release for main consumption yet... so wondering if you are in a test slice or something else. 

Do a test, as the BIOS Post is finishing, start pressing your <left-shift> key intermittently. When your grub menu shows... <Arrow-down> to the other kernel submenu option. Select that, then select the last kernel and boot. Tell me if that starts your desktop with graphics.

---

### Post by Malcolm_Brown on 2015-01-18
Thank you for giving up your time to help!

When I select the second line 'Advanced options' I get a long list starting with Linux 3.13.0-44 generic, then in turn 43, 40, 39, 37, 36, 35, 34, 32.  Selecting any of these results in a black blank screen.

I attach the sources.list file as requested.

I could not find the file libc6:i386.  I looked in lib and lib/i386-linux-gnu.  The latter had a file libc.so.6 of 1.8Mb but was impossible to copy as it only gave 32 characters and would not upload.  I don't know if this is the file you were referring to.

I tried the Shift Left arrow but could not get it to work and wondered if I was pressing the correct keys.

---

### Post by Malcolm_Brown on 2015-01-20
I have looked at the GRUB menu and I have this version.....

GNU GRUB version 2.02^beta2-9ubuntu1

A line in it says .....      linux /boot/vmlinuz-3.13.0-44-generic

Not certain if that helps, but hope it does!

---

### Post by MAFoElffen on 2015-01-20
On boot, at the Grub menu > Press the <E> key. That will put you into edit mode. Go to the end of that kernel boot line that starts with "linux" and append with 
```

nomodeset

```
Then press <cntrl><X> to boot... see if that works... 

Intel drivers in Xorg are opensource. Intel provides their own source for their GPU's. They usually do not have troubles... I note "usually." There have been times when their provide was wrong or that the code hadn't caught up in time...

---

### Post by greenthumb88 on 2015-07-08
> **MAFoElffen said:**
> I see that Xorg says your driver loaded, and said it had no errors... but you are getting a black screen. 
So in your upgrade was linux-image-generic:i386 (3.13.0.43.50, 3.13.0.44.51) and libc6:i386 (2.19-0ubuntu6.4, 2.19-0ubuntu6.5)... You didn't have an XServer update, so still running the same xserver-xorg-video-intel 2:2.99.910-0ubuntu1.3 driver that was before that update.

Could you post your sources.list... or check it yourself and see if your have proposed selected for some reason... I see that kernel update as proposed but not release for main consumption yet... so wondering if you are in a test slice or something else. 

Do a test, as the BIOS Post is finishing, start pressing your <left-shift> key intermittently. When your grub menu shows... <Arrow-down> to the other kernel submenu option. Select that, then select the last kernel and boot. Tell me if that starts your desktop with graphics.

I'm having a similar issue, but after booting with a different kernel I did have graphics at boot. I'm not sure why it worked this time, and would like help fixing the newer kernel if that is the issue.

---

### Post by greenthumb88 on 2015-07-08
seems like the lasted update messed with my xorg drivers. booted using  proprietary and drivers and all is good for now.

---

