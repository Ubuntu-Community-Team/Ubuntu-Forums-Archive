---
title: "Studio 12.04 Install DVD Won't Boot"
date: 2012-06-04
forum: Installation &amp; Upgrades
---

### Post by MrBalloonHands on 2012-06-04
So I made a Ubuntu studio 12.04 install DVD, made my pc boot from the DVD drive first, and when I try to boot from the DVD, a small pinking line appears in the top left hand corner of my screen for a few seconds then disappears and boots to Windows 7. 

I thought at first it was a bad burned DVD, but I made 2 copies with the same results. 

Is there something up with the Studio DVDs? Or can I install regular Ubuntu and then upgrade it to studio from there?

Thanks ahead for the help,

-Nate

---

### Post by CrocoDuck on 2012-06-04
Hi. Make sure you have the cd drive at top position in the boot order (your bios setup). Depending on what computer you have you may have to hit some key combination in order to choose the device to use for boot. Have a look at your computer manual. If you are sure that boot order is ok maybe (as you said) we have a bad burned dvd... Have a look if your .iso is corrupted and try to burn as better you can (if I'm not wrong is better with lower speed).

Of course you can install ubuntu studio packages, but you have to do a little work to tune your system (install lowlatency or realtime kernel first, install jack and qjackctl, configure users groups and some configuration file... and then the cool packages you need). Nothing impossible, of course... you just need a little more time. There are also meta packages for install all the ubuntu studio stuff (complete with kernel) on your standard ubuntu (by simply using software center, apt or synaptic)... I never used them.

For upgrade from a standard ubuntu to ubuntu studio you can follow this guide: [https://help.ubuntu.com/community/UbuntuStudioPreparation](https://help.ubuntu.com/community/UbuntuStudioPreparation)

---

### Post by MrBalloonHands on 2012-06-04
Ok I'll try that. Is it possible that since I used i386 versus amd64 could cause the issue? I have an intel motherboard, so I figured i386 would be the right choice.

---

### Post by lbthrice on 2012-06-04
Hi,

I also have a Dell Studio that will not boot the 12.04 (x86) ubuntu desktop image from image from DVD or USB bootable media.

I have set the boot order, with usb drive and cd/dvd-w drive in the first and second position, respectively.

If you have found a solution, please let me know.

In the meantime I am going to re-download the image in case I have errors in my file.

---

### Post by CrocoDuck on 2012-06-04
> **MrBalloonHands said:**
> Ok I'll try that. Is it possible that since I used i386 versus amd64 could cause the issue? I have an intel motherboard, so I figured i386 would be the right choice.

i386 should work with all architectures. When the booting process works successfully, if there is an issue with the architecture, the loaded program should prompt an error message. You have to choose between i386 and amd64 depending on your CPU (if 32 bit or 64 bit). 32 bit processors can't run 64 bit OS. Viceversa is allowed (32 OS on 64 CPU is ok). I'm usually install amd64 on computers with 64 bit CPUs and i386 on computers with 32 bit CPUs, the natural choice.


> **lbthrice said:**
> Hi,

I also have a Dell Studio that will not boot the 12.04 (x86) ubuntu desktop image from image from DVD or USB bootable media.

I have set the boot order, with usb drive and cd/dvd-w drive in the first and second position, respectively.

If you have found a solution, please let me know.

In the meantime I am going to re-download the image in case I have errors in my file.

If you have linux (but you can install utilities that let you behave like this on mac os and windows too) try the checksum of the image you downloaded:

Open a terminal, go in the directory where you saved the .iso file and then:

```
md5sum ubuntu-12.04-dvd-i386.iso
```

If ubuntu-12.04-dvd-i386.iso is the iso, for example, that you downloaded (naturally, you have to put the name of the .iso you want to check. Thus, if you downloaded ubuntu-12.04-server-i386.iso, the command sounds like md5sum ubuntu-12.04-server-i386.iso ).

The output will be a code. Check if the code is esactly the one you can find here for your iso: 

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

If the codes match, then your iso isn't corrupted. In the same page you can find links to detailed descriptions on md5sum and burning iso.

---

### Post by lbthrice on 2012-06-04
Hi,

My md5sum matches; I do not have a corrupted image.
This is strange.
Previously, I installed Natty on this machine with no issues.

Thank you for your help.

---

### Post by lbthrice on 2012-06-04
Great news everyone!

I am posting now from my brand new precise pangolin install.

All I had to do was use the "Boot Options" menu from the bios and explicitly select the USB drive for bootloading.

[B]So Mr. Balloon Hands, you should try to press f12 at the boot screen and then select cd/DVD drive from the boot options.
This should work for you.[/B]

For posterity, I would like to reiterate that I had already configured the boot sequence in the BIOS setup menu (accessed with f2 keypress) but the bootable usb was ignored. I am not sure why the boot options menu (accessed with f12 keypress) did work but the setup menu did not.

thanks CrocoDuck!

---

### Post by CrocoDuck on 2012-06-05
> **lbthrice said:**
> Great news everyone!

I am posting now from my brand new precise pangolin install.

All I had to do was use the "Boot Options" menu from the bios and explicitly select the USB drive for bootloading.

[B]So Mr. Balloon Hands, you should try to press f12 at the boot screen and then select cd/DVD drive from the boot options.
This should work for you.[/B]

For posterity, I would like to reiterate that I had already configured the boot sequence in the BIOS setup menu (accessed with f2 keypress) but the bootable usb was ignored. I am not sure why the boot options menu (accessed with f12 keypress) did work but the setup menu did not.

thanks CrocoDuck!

Very happy you figured out how to boot!!! I remind to **MrBalloonHands** that the boot options may be accessible on your machine by hitting a different key than f12, as I said in the first reply (for my laptop, for example, I hit esc to open the boot screen). Refer to your computer manual or google your computer model in order to know exactly how to behave.

> **CrocoDuck said:**
> ...Depending on what computer you have you may have to hit some key combination in order to choose the device to use for boot...

---

