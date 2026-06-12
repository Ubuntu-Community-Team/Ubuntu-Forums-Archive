---
title: "When trying to get on to live desktop i get the console ."
date: 2011-12-03
forum: Installation &amp; Upgrades
---

### Post by Max4344 on 2011-12-03
I am trying to install Ubuntu 11.10 by CD and USB on my Acer Aspire 1 ZA3 and when it finishes booting up it brings me to this console. 

Yet 11.04 works without any errors and I can run KDE 4 on it.

I tried to install Xubuntu 11.10 by CD and still get the same error.

---

### Post by dabl on 2011-12-03
You're going to have provide WAY more information before anyone is going to be able to help.

- does the Live CD run correctly on your hardware?
- what is the motherboard (or computer model), CPU, memory, and video/GPU?
- how big did you make the root partition, what filesystem?
- did you md5sum check the downloaded ISO and CD?
- what is the monitor/display?

---

### Post by dabl on 2011-12-03
> **dabl said:**
> 
- what is the motherboard (or computer model)

Upppps, I see it is an Acer Aspire 1 ZA3.  So, you should probably start with a thorough review of this:  [https://help.ubuntu.com/community/AspireOne](https://help.ubuntu.com/community/AspireOne)

---

### Post by Max4344 on 2011-12-03
> **dabl said:**
> 
- does the Live CD run correctly on your hardware?
No it brings me a console when it finishes booting up the live CD thats what i ment by live desktop
> **dabl said:**
> 
- how big did you make the root partition, what filesystem?

I dont know how to check it on Windows but assuming the root is the ubuntu. Than i dont install it locally i install to a 16gig microSDcard.
> **dabl said:**
> 
- did you md5sum check the downloaded ISO and CD?

No But i did test it on a another system(with virtual box) and it worked even installed without errors.

---

### Post by dabl on 2011-12-04
When you boot the Live CD, and the first text menu comes up, try pressing F6 "Safe Graphics".  If that works, you'll know that the issue is that you need to use a "boot code" -- a kernel boot code that disables some part of the standard kernel module configuration that is not right for your hardware.

---

### Post by Max4344 on 2011-12-04
> **dabl said:**
> When you boot the Live CD, and the first text menu  comes up, try pressing F6 "Safe Graphics".  If that works, you'll know  that the issue is that you need to use a "boot code" -- a kernel boot  code that disables some part of the standard kernel module configuration  that is not right for your hardware. I will try that.
EDIT: on Ubuntu(and Xubuntu) it doesnt say Safe Graphics it shows me ramdom stuff(acpi=off,noapic,nolapic,edd=on,nodmraid,nomodeset,Free Softwere Only)

---

### Post by MAFoElffen on 2011-12-05
> **Max4344 said:**
> I will try that.
EDIT: on Ubuntu(and Xubuntu) it doesnt say Safe Graphics it shows me ramdom stuff(acpi=off,noapic,nolapic,edd=on,nodmraid,nomodeset,Free Softwere Only)
Arrow down to nomodeset. Press the spacebar to select it. Press escape to get back to the advanced menu. Select "Try."

If it doesn't, then also add acpi=off to nomodeset. Also might try xforcevesa or vesa=792

If that doesn't work- Reboot and get back to the Advance Install Menu. Press escape. It will display a message saying "leaving the graphical install menu and entering the text install menu." It will probe the graphics and do one of 3 things.
- Go the the text install.
- Error and say :could not determine mode xxx, then display a text menu for you to select a mode (I usually select the last option which is 640x480x16.
- Error and go back to the Advance Menu
- Error and go to a prompt.

Usually, in the rare times it "I" can't get it working through any of those (and I do know a lot of work arounds!!!) Then I'll use an Alternate Install CD or a Minimal Install CD, which are both text-based installers.

---

### Post by Max4344 on 2011-12-05
> **MAFoElffen said:**
> Arrow down to nomodeset. Press the spacebar to select it. Press escape to get back to the advanced menu. Select "Try."

If it doesn't, then also add acpi=off to nomodeset. Also might try xforcevesa or vesa=792

If that doesn't work- Reboot and get back to the Advance Install Menu. Press escape. It will display a message saying "leaving the graphical install menu and entering the text install menu." It will probe the graphics and do one of 3 things.
- Go the the text install.
- Error and say :could not determine mode xxx, then display a text menu for you to select a mode (I usually select the last option which is 640x480x16.
- Error and go back to the Advance Menu
- Error and go to a prompt.

Usually, in the rare times it "I" can't get it working through any of those (and I do know a lot of work arounds!!!) Then I'll use an Alternate Install CD or a Minimal Install CD, which are both text-based installers. Acpi=off with nomodeset Makes a Gray screen but i hear the log in sound. Do i also try xforcevesa with nomodeset and acpi=off?

---

### Post by MAFoElffen on 2011-12-05
> **Max4344 said:**
> Acpi=off with nomodeset Makes a Gray screen but i hear the log in sound. Do i also try xforcevesa with nomodeset and acpi=off?
" nomodeset " <-- alone, if you have Nvidia, but also works for some other cards.
" nomodeset acpi-off " <-- works on some latops
Those 2 are in the F6 menu. For others, press F6, then escape. Youll see a boot line below the menu with a flashing cursor. There you can add boot options manually, such as:
" xforcevesa " <-- alone, is the same as failsafe video
" vesa=792 " <-- alone, tell X to use a VESA mode of 1024x768x24 bit
" vesa=791 " <-- Same as above but as 1024x768x16 bit.
" radeon.modeset=0 " <-- use for machines with Radeon Cards
" nouveau.modeset=0 " <-- use for machines with Nvidia
" i915.modeset=0 <-- use for machines with older intel video.

Is that enough to try for awhile?

---

### Post by Max4344 on 2011-12-06
> **MAFoElffen said:**
> " nomodeset " <-- alone, if you have Nvidia, but also works for some other cards.
" nomodeset acpi-off " <-- works on some latops
Those 2 are in the F6 menu. For others, press F6, then escape. Youll see a boot line below the menu with a flashing cursor. There you can add boot options manually, such as:
" xforcevesa " <-- alone, is the same as failsafe video
" vesa=792 " <-- alone, tell X to use a VESA mode of 1024x768x24 bit
" vesa=791 " <-- Same as above but as 1024x768x16 bit.
" radeon.modeset=0 " <-- use for machines with Radeon Cards
" nouveau.modeset=0 " <-- use for machines with Nvidia
" i915.modeset=0 <-- use for machines with older intel video.

Is that enough to try for awhile?
Nothing Works.
I really would like to know why does 11.04 works and 11.10 just doesnt work.

---

### Post by MAFoElffen on 2011-12-06
> **Max4344 said:**
> Nothing Works.
I really would like to know why does 11.04 works and 11.10 just doesnt work.
Something is bugging me about htis... If 11.04 works for you and you are doing a clean install- Why aren't you installing 11.04, install drivers, then do a do-release-upgrade to get it to 11.10.

---

