---
title: "fglrx is working, from the menu sys-admin-hardware driver"
date: 2008-10-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by sdowney717 on 2008-10-15
in fact it was painless to enable it. no messing with xorg.conf
no having to run aticonfig-initial.
it just plain worked.
that is great.

---

### Post by Merovius on 2008-10-15
Working for me to finally. I was not as lucky though. I had to mess around for quite a while. I did some updates while I was messing with it and I think that did it.

I can finally use my 1650 Pro!

---

### Post by Merovius on 2008-10-16
After reboot it's DOA again. Back to 2d mode..:confused:

---

### Post by sdowney717 on 2008-10-16
i have an x1300 pro.
no messing around with any configs for me.

did you have any prior fglrx or nvidia binaries on the machine? you can see that using synaptic. I was running a pure free driver with no prior installs of nvidia or fglrx binary drivers. I actually had purged these out of the system in Hardy.

you can try purging the system and you can also
READ the xorg.log in /var/log and it might give some info. errors are shown with an 'EE' flag

---

### Post by Merovius on 2008-10-16
The log shows this error;

(EE) RADEON(0): [dri] RADEONDRIGetVersion failed because of a version mismatch.
[dri] radeon.o kernel module version is 8.54.3 but version 1.17.0 or newer is needed.
[dri] Disabling DRI.

Any ideas?

---

### Post by Merovius on 2008-10-16
I just had the hardware drivers app activate the driver and rebooted twice successfully. I also noticed the catalyst control center is in applications. Don't remember seeing it before. We'll see how it goes tomorrow.

Thanks for all suggestions.

---

### Post by zoomy942 on 2008-10-16
im just hoping for the day the intel x3100 gets some 3d....  doesnt the ubuntu team realize how many people have this chipset in their laptops?

---

### Post by inportb on 2008-10-16
Slightly off-topic? fglrx is maintained by AMD, which is not responsible for Intel drivers.

---

### Post by scradock on 2008-10-16
> **Merovius said:**
> I just had the hardware drivers app activate the driver and rebooted twice successfully. I also noticed the catalyst control center is in applications. Don't remember seeing it before. We'll see how it goes tomorrow.

Thanks for all suggestions.

I tried the new fglrx driver, but found the display choppy, and got a lower frame-rate on glxgears. Switched back to the free driver ati/radeon. Compiz and Flash video seem to work fine, so I'm not desperate for fglrx - though it is good to see it working with the new xorg.

---

### Post by zoomy942 on 2008-10-16
> **inportb said:**
> Slightly off-topic? fglrx is maintained by AMD, which is not responsible for Intel drivers.


i know.  im just salty that intel x3100 users are left in the lurch  :lolflag:

---

### Post by Merovius on 2008-10-17
Well, same thing different morning. Desktop was just wallpaper this morning. Had to go back to 2d mode to get any panels or icons.

Seems it does work, it just doesn't "stick" after a reboot or two.

---

### Post by sdowney717 on 2008-10-17
when it works do you still have that error in the xorg.log?
I believe there are a few older logs kept in their as well.
you must boot the latest kernel 2.6.27-7 for it to work.

I tried booting older kernel 2.6.26 and fglrx would not load. But I got a normal 2d desktop with no 3d.

curious, what is your intel chipset? 

I am still going strong with the beta fglrx the ubuntu team got ATI to release ahead of time.

---

### Post by Merovius on 2008-10-17
I'll have to check the log if I get it going tonight when I'm home. As far as I know I am booting the newest kernel.

It's another poster with the Intel stuff.

---

### Post by Merovius on 2008-10-17
I finally got it to install for the 3rd night after removing anything to do with compiz. 

It has booted twice to a normal desktop. No errors in the /var/log anymore.

But, now TVTime does not work anymore. ??  Reinstalled it to no avail.

Maybe I will try installing the compiz stuff *after* the driver instead of before..

---

### Post by Merovius on 2008-10-17
Installed Compiz after the new ATI driver and was able to reboot to a functional desktop twice.

TVTime still refuses to show video. The first couple times the driver was installed (after Compiz) and wouldn't stick TVTime worked but was a little jerky. Now the driver seems to be working OK but TVTime won't.

:confused:

---

### Post by Merovius on 2008-10-18
Well, I finally decided that ATI is still not ready for prime time.

 I reinstalled my Nvidia 6800XE and installed the proprietery driver enabled desktop effects and all works fine first try. TVTime and any other video anomalies are good now.

Thanks for all the help and ideas to all.

---

### Post by ercdvs on 2008-10-18
I pulled the newest ATI driver today as well, and it borked hibernate.

  640.580738] PM: Creating hibernation image: 
[  640.584208] PM: Need to copy 138844 pages
[  640.584208] PM: Normal pages needed: 128031 + 1024 + 24, available pages: 112085
[  640.584208] PM: Not enough free memory
[  640.584208] PM: Error -12 creating hibernation image


Twas odd becuase everything was fine up until the ati driver install..  time to play a bit more

---

