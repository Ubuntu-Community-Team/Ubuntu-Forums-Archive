---
title: "[SOLVED] Ibex horribly broken won't boot"
date: 2008-07-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by spamzilla on 2008-07-05
I just installed kernel *.3, 60~ other updates and restarted. On bootup, the graphics is all scrambled and quite alarmingly moves around the screen. Then the login screen usually fails to display, but if it does display and I login, I see my desktop background shortly followed by a white screen - something similar to what compiz used to do. The virtual terminals lockup when I try to switch to them and I'm forced to do a hard restart.

Kernel's *.2 and *.3 are now unbootable but thankfully my XP partition still works fine.

Has this happened to anyone else? Could this be a graphics chip (intel x3100 965) / compiz issue?

---

### Post by nIRV on 2008-07-05
spamzilla, I don't see the scrambling graphic issue but I'm also having the failure to display screen at login and the white screen.

re white screen, it started happening after I updated intrepid this am with latest packages including mesa driver and drm kernel module, the two I'm guessing is causing problem. you can fix problem by disabling compiz (run in failsafe mode)

re failure to display screen, I noticed issue since update from hardy to intrepid, unsure whether it's a kernel issue or latest intel driver. haven't found any solution to this except rebooting machine.

my graphic guard is similar to yours.

---

### Post by plun on 2008-07-05
> **spamzilla said:**
> 

Has this happened to anyone else? Could this be a graphics chip (intel x3100 965) / compiz issue?

Nope... works Ok for me with the patched nVidia driver with a nVidia card.


"FWIW", For Intel I noticed that xorg-server 1.5 must have failed to build. :(

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html)


Mesa and the new kernel are Ok but maybe it is a "mismatch" with Xorg for Intel owners ...:confused:

---

### Post by spamzilla on 2008-07-05
> **nIRV said:**
> re white screen, it started happening after I updated intrepid this am with latest packages including mesa driver and drm kernel module, the two I'm guessing is causing problem. you can fix problem by disabling compiz (run in failsafe mode)

Ugh why didn't I think of doing this? Must be the hangover :lolflag: Thanks!! 

> **plun said:**
> Nope... works Ok for me with the patched nVidia driver with a nVidia card.


"FWIW", For Intel I noticed that xorg-server 1.5 must have failed to build. :(

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html)


Mesa and the new kernel are Ok but maybe it is a "mismatch" with Xorg for Intel owners ...:confused:

Hmm ok thanks for the info.

---

### Post by ronacc on 2008-07-05
I can confirm what plun said , updated this AM and got the .3 kernel etc and it works ok with the patched nvidia driver . sidenote: aptitude wanted to remove the .2 kernel headers but not the .2 kernel itself , I copied the headers to a safe place before proceeding incase a "fallback" was necessary .

---

### Post by Nullack on 2008-07-05
Ronacc can you boot high res / colour depth from grub with -3? I cant

---

### Post by autocrosser on 2008-07-05
I used Synaptic to update & it left my .2 stuff alone--Patched the beta 177 Nvidia driver & all seems to be working OK. Usplash is just a black screen--I can watch my hard drive activity light until GDM ;)

Had a .xsessions-error yesterday--kept me out of all my users for a bit--I normally enable the root user & allow login via GDM for root--allowed me a easy way to fix the permissions problem (/tmp changed permissions, all my icons went generic & the desktop froze--not too fun :)  ). This was on a fresh install from earlier this week--not sure what caused it.......

---

### Post by ronacc on 2008-07-05
> **Nullack said:**
> Ronacc can you boot high res / colour depth from grub with -3? I cant

haven't tried , I leave grub at the defaults .if you mean gdm as booted yes 1440x900x24 .

---

### Post by mitchellcipriano on 2008-07-05
I did the update today and I have had no problems in VBox. I did need to reinstall the guest additions.

---

### Post by Nullack on 2008-07-05
> **ronacc said:**
> haven't tried , I leave grub at the defaults .if you mean gdm as booted yes 1440x900x24 .

No I mean before gdm

---

### Post by autocrosser on 2008-07-05
Spamzilla--looks like you might be having the same problems I have had--take a look at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

I get no screen sometimes during boot & sometimes a number of different "issues"

---

### Post by xebian on 2008-07-05
> **autocrosser said:**
> Spamzilla--looks like you might be having the same problems I have had--take a look at:  [https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/235662)

I get no screen sometimes during boot & sometimes a number of different "issues"

Could not even get past grub - file not found, though perfectly ok with -2.:confused::confused::confused:

---

### Post by autocrosser on 2008-07-05
What grub error number are you getting? I got a .xsessions-error yesterday & then I "lost" grub with a error 15---followed by a "lost" drive in the bios--all with a almost new MB & SATA drive---all-in-all, not a fun day :(

---

### Post by xebian on 2008-07-05
> **autocrosser said:**
> What grub error number are you getting? I got a .xsessions-error yesterday & then I "lost" grub with a error 15---followed by a "lost" drive in the bios--all with a almost new MB & SATA drive---all-in-all, not a fun day :(

It's the file not found : error 15.  So how did you get around it?  I saw an extra new file in /boot - vmcore-kernel-version-generic but somehow it disappeared after a few reboots.  :confused:

---

### Post by autocrosser on 2008-07-05
I did the "dance" with a LiveCD & reinstalled grub--seems that grub "lost" where my stage 1 was ;) .  Boot up a Live & mount your drive that has /boot/grub on it--then in a term do a sudo grub. At Grub prompt> find /boot/grub/stage1
then >root (hd "where /boot/grub is") then >setup (hd0) then >quit. (not a good dance step--but effective).

You "should" be back in business--if not, you will need the Super Grub boot disc--look in the Tutorial forum for the address--I don't remember it.....

---

### Post by Gina on 2008-07-06
I ran the update on my laptop last night but GRUB didn't update (even though Intrepid is the last install) and the choice of kernel hasn't changed.  Have to update grub manually.

---

### Post by nIRV on 2008-07-06
> **plun said:**
> Nope... works Ok for me with the patched nVidia driver with a nVidia card.


"FWIW", For Intel I noticed that xorg-server 1.5 must have failed to build. :(

[https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-July/002952.html)


Mesa and the new kernel are Ok but maybe it is a "mismatch" with Xorg for Intel owners ...:confused:

looks to me this might very well be the issue with intel graphic card owner.

/me awaiting package...

---

### Post by Malac on 2008-07-06
Just updated to .3 and had the white screen on login from compiz.
ATI RADEON 9200SE. if this is any help.

---

### Post by eeclark on 2008-07-06
> **Malac said:**
> Just updated to .3 and had the white screen on login from compiz.
ATI RADEON 9200SE. if this is any help.

At this point, my question is what is causing the white screen?
Is it the ATI (opensource-radeon) driver? Is it compiz?
I know I can use metacity to get around the issue, but I am curious as to what is causing the problem.

---

### Post by spamzilla on 2008-07-06
> **eeclark said:**
> At this point, my question is what is causing the white screen?
Is it the ATI (opensource-radeon) driver? Is it compiz?
I know I can use metacity to get around the issue, but I am curious as to what is causing the problem.

I presume its compiz since the same problem is happening on different graphics cards/chips (intel and ati / radeon).

---

### Post by BCurtisWX on 2008-07-06
> **spamzilla said:**
> I presume its compiz since the same problem is happening on different graphics cards/chips (intel and ati / radeon).

If you do a cntrl+f5 when u get the white screen, then do a ps -e | grep compiz and sudo kill -9 "PID for compiz.real", that is a temp fix (it disables compiz, which seems to be the main problem.)

---

### Post by psyke83 on 2008-07-06
> **BCurtisWX said:**
> If you do a cntrl+f5 when u get the white screen, then do a ps -e | grep compiz and sudo kill -9 "PID for compiz.real", that is a temp fix (it disables compiz, which seems to be the main problem.)

I would say these recent compiz problems are due to Mesa 7.1rc being uploaded without the new build of Xorg available that it depends on to function correctly.

---

