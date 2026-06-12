---
title: "Ubuntu 10.4 installation on thinkpad x40 - fail"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by mcjibs on 2010-06-15
I'm trying to install ubuntu 10.4 onto a previous windows based laptop (ibm thinkpad x40)

I've tried a bootable cd but that did not work. I finally tried using a ubb drive. The installation went through and it ended successfully. When I tried to reboot, an ubuntu start screen came up and then it goes completely blank. - There is no sound indicating that it's starting up and I am just not seeing it. - I tried plugging into an external monitor to see if its resolution problem - but that did not work as well.

Please help.

---

### Post by rob45 on 2010-06-15
Have you tried running the low graphics option thats available...i think...if you boot into safe mode...by pressing tab or escape..there should be an option for a low graphics....then once your in ubuntu...you can sort out your drivers...??

---

### Post by mcjibs on 2010-06-26
Hey Rob,

I'm trying the installation from a bootable cd now on a different ibm thinkpad x40.
It currently running windows xp and graphics card is an intel chipset.

At startup, I see the Ubuntu with the standard orange dots running across and I could hear the dvd working hard a good minute. It then stops and the everything goes blank. 

There is no more sound from the cd/dvd drive and no hard drive activity lights.

It just sits there forever as is.

any help would be appreciated.

---

### Post by mcjibs on 2010-06-26
I just tried something else and I finally got to the installation screen. I went through the seven steps and it is installing right now.  - hopefully this works!!

These are the steps i followed:

1) At the purple screen with a keyboard and  stickfigure, press Enter to get to the menu. 
2) Hit Enter to select your language, and then press F6  and then Esc. 
3) Add  "i915.modeset=1" after "quiet splash". 
4) Press  Enter to boot the LiveCD.

---

### Post by mcjibs on 2010-06-26
So the installation went to completion and I restarted the computer. I briefly see the Unbuntu screen come up with the orange dots and then I just see a blank screen. - no sign of hard drive activity either.

---

### Post by mcjibs on 2010-06-28
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

I  tried the first workaround by adding i915.modeset=1 after quiet splash  for both the installation and the login of ubuntu. It actually worked!  Then the forum says that "If adding "i915.modeset=1" to your boot  parameters allows you to boot  successfully, you then need to enter the command above into a terminal  to make the changes permanent."

I don't know how to do this - I'm  hoping you can help. I don't know linux commands and I am hoping you  can help. When I go to the terminal window it shows me "grub >"

If anyone knows how to make the boot parameter permanent, please let me know.

---

### Post by mikeh on 2010-09-30
> If anyone knows how to make the boot parameter permanent, please let me know. 

Its not very clear, but you use the commands given earlier on the same page:

> echo options i915 modeset=1 | sudo tee /etc/modprobe.d/i915-kms.conf
sudo update-initramfs -u


I have done this, and 10.04 now runs. With compiz, suspend and hibernate, but using Xv (video accel) causes the display to lock up.

Has anyone found a fix for this?

Will try 10.10 beta.

---

