---
title: "Kernel ATI flicker on HP nc8430"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Insane_Homer on 2010-03-23
I've been running 10.04 for a month or 2 without issue, however this week I got a really outrageous screen clicker.

I waited a few days for a few more updates to see if that solved the problem but to date that's not helped.

On the 32-bit version I've found that booting to Kernel 2.6.32-17 and 2.6.32-16 both exibit the same problem.

2.6.32.13 Generic is fine.

The flicker appears be a problem with the chip overclocking/frequency. Possibly causing over heating as it seemed to get worse the longer it kept going.

gfx drivers are base install for 10.04 no tweaking or mods.

It happens under KDE & Gnome and starts at the GDE login screen.

---

### Post by Insane_Homer on 2010-04-03
After the latest sets of updates, still only able to get a stable image and flicker free display on -13 Kernel or earlier.

No one else experiencing these problems?

---

### Post by homburg on 2010-04-03
I'm experincing flickering and overheating on my Acer TravelMate 4220 as well.

The graphics adapter is Ati Mobility X1300.

It seems to be especially bad on external (vga connector) displays.

---

### Post by fishwithapipe on 2010-04-03
Confirmed for me also on nc8430, kernel version 2.6.32-14 works, but -18 and -19 both flicker like crazy.

further searching has revealed this thread :
[http://ubuntuforums.org/showthread.php?t=1428550](http://ubuntuforums.org/showthread.php?t=1428550)
and this bug id on launchpad :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/538344)

---

### Post by The Glitch on 2010-04-08
Same problem here.  NC8430 with Radeon X1600.  Using 10.04 desktop Beta 1.

---

### Post by kluffinator on 2010-04-09
I've got this problem as well--except I've got a Mobility X1270. I've been having flickering issues even with the earlier kernels, however. 

I managed to solve this by adding the -nomodeset parameter to the kernel on boot but, on 2.6.32-19, it persists even without KMS.

I hope there'll be a fix.

---

### Post by sdm_cacto on 2010-04-09
> **kluffinator said:**
> I've got this problem as well--except I've got a Mobility X1270. I've been having flickering issues even with the earlier kernels, however. 

I managed to solve this by adding the -nomodeset parameter to the kernel on boot but, on 2.6.32-19, it persists even without KMS.

I hope there'll be a fix.

Same graphics, same problem here. Try radeon.modeset=0 on grub, it fixes it.

---

### Post by cariboo on 2010-04-09
Has anyone filed a bug?

---

### Post by mattisking on 2010-04-09
> **sdm_cacto said:**
> Same graphics, same problem here. Try radeon.modeset=0 on grub, it fixes it.

Thank you! I spent forever on this last night. The nomodeset used to work but stopped after recent updates. This, however, works great. Thanks again.

---

### Post by sdm_cacto on 2010-04-11
> **cariboo907 said:**
> Has anyone filed a bug?

I think this one qualifies:
 > [https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501](https://bugs.launchpad.net/ubuntu/lucid/+source/linux/+bug/541501)



no problem mattisking , check out that bug and see if you can help

---

### Post by The Glitch on 2010-04-12
As suggested in the above link, adding radeon.new_pll=0 to the kernel at boot time fixed it for me.  For a permanent fix here is what I did (IIRC):

sudo vi /etc/default/grub 
 set: GRUB_CMDLINE_LINUX="radeon.new_pll=0"  
sudo update-grub

---

