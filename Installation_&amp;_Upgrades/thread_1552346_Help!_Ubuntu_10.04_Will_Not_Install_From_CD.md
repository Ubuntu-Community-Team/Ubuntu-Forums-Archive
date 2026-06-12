---
title: "Help! Ubuntu 10.04 Will Not Install From CD"
date: 2010-08-13
forum: Installation &amp; Upgrades
---

### Post by andreab35 on 2010-08-13
Hello everyone!

Whew, I haven't been here in a while! But now I've come back with a big problem.

I will be migrating my father's laptop from Windows XP to Ubuntu 10.04. I downloaded the .iso, burnt it successfully onto a DVD twice at 6x speed with my Mac. 
When I put the CD in, the ubuntu screen comes up and looks like it's working (you know, those moving dots). After that's finished, the CD totally stops and the screen goes blank, but the laptop is still running - but doing nothing. 

I tried installing the boot screen from the CD while running Windows. That was successful, but the same exact thing happens when I try to go into Demo mode or try to install the OS.

This laptop is a Gateway M275. I've run Ubuntu 9.x on this before, but I can't figure out what's going on with this one.

Any help would be appreciated. Thanks!

---

### Post by davidmohammed on 2010-08-13
Plug in the live CD - when booting, press any key and you should be presented with 6 options.

Press either F6 or tab (I think) - add one of the following

nomodeset 
i915.modeset=1
i915.modeset=0

BEFORE quiet splash

press the option to boot.

Hopefully you will get to the desktop.

 When rebooting, dont forget to edit your grub (press e when grub is displayed) and add the boot option you have found.

---

### Post by andreab35 on 2010-08-13
Thanks! Let me give that a shot and I'll update you if that works. :)

UPDATE: Nope, still not working. I'm getting the same exact issue like I did before. :(

---

### Post by aago1254 on 2010-08-15
> **andreab35 said:**
> Thanks! Let me give that a shot and I'll update you if that works. :)

UPDATE: Nope, still not working. I'm getting the same exact issue like I did before. :(

well i had the same issue with the same model, i said well let me do 9.10 and install that works good i update the updates does the same as the 10.04 cd. so i reinstalled 9.10 and did a distribution upgrade this time same thing the cd gave me. 

i have tried the following linux disks.

lubuntu 10.04, puppy 5.0.1 , kubuntu 10.04, i think something in the new grub is causing the issue or something in the kernel not playing nice with the model of computer

---

### Post by dubie18 on 2010-08-15
I have the same issue, I tried the nomodeset change, and it worked that one time to get me into the system, but every time I restarted it just sent me to a blank screen, and I had to reinstall it.  I tried downloading the driver for the video card, but when i rebooted it lost it and went back to the blank screen again.

---

### Post by davidmohammed on 2010-08-15
dubie18 - when you reboot, you have to redo the nomodeset change.  If you want to fix the nomodeset permanently then try the following

boot with nomodeset as explained above.

open a terminal session.

type 

sudo nano /etc/default/grub

change the line
GRUB_CMDLINE_LINUX=""

to read

GRUB_CMDLINE_LINUX="nomodeset"

save

then run


sudo update-grub

---

### Post by davidmohammed on 2010-08-15
> **andreab35 said:**
> Thanks! Let me give that a shot and I'll update you if that works. :)

UPDATE: Nope, still not working. I'm getting the same exact issue like I did before. :(

...others have found that downloading the [alternate CD]("http://releases.ubuntu.com/lucid/") that has the text installer works better than the live CD.

---

### Post by dubie18 on 2010-08-15
Ok, so when I run sudo update-grub it gives me an error: cannot find a device for / (is /dev mounted?).

When I install it, i have to exit out of the restart now? question at the end of the install, otherwise when it restarts it goes to the blank screen again.  That's when I'm trying the nomodeset.

I also tried installing the alternate installer, and it still showed me a blank screen on restart.

---

