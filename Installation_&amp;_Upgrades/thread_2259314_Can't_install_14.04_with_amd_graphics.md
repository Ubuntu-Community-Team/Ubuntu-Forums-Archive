---
title: "Can't install 14.04 with amd graphics"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by steve181 on 2015-01-03
I have an asus motherboard with an amd a6800k CPU, I had no problems with version 13 but upgrading and even doing a fresh install just boots up to a black screen, I know there are problems with the graphics drivers but I can't find a fix anywhere, and when I go into  bios I have 3 options to boot from with ubuntu and I can't figure out why, one of them brings me to grub recover and the other 2 just go to black screen. , if anyone can point me in the right direction it would be greatly appreciated, it's not even giving me an error message that I can google.

---

### Post by MAFoElffen on 2015-01-03
On an installed system- 
1. If you have a multi-boot yss installed skip #2
2. At just as the BIOS messages pass, start intermittently pressing the <left-shift> key. 
3. When the Grub Menu appears, prees <E> to enter an edit mode
4. While in edit mode, <Arrow-Down> to Linux Boot line. It starts with "linux". 
5. <Arrow-Right> to the end of the line.
6. ** append the end of that line with the kernel boot option "radeon.modeset=0".
7. Press <cntrl><X> to boot
8. After boot. Install your driver from: System Settings > Last tab, Additional Drivers... Or any other method you are comfortable with (More info in the first 2 post of my sticky, link in my signature line)

Tell me how it goes and ask question if you have them...

---

### Post by steve181 on 2015-01-03
Thanks for responding? I can't access the grub menu, but I can't access the grub menu using that for some reason, I got it to boot right now using fail safe graphics mode, can I edit that file from the command line? I have  /boot/grub/ grub.cfg open right now and also etc/default/grub open. But I know I can't edit the /boot/grub/grub.cfg , or can I find it in /etc/grub.d.  Here is a picture of etc/default/grub. , or am I in the totally wrong place

---

### Post by MAFoElffen on 2015-01-03
If you are that far, just go to System settings > Last Tab of that is Additional Drivers... from there, if drivers are still selected. remove. Then or if not, install what is recommended.

The reason (if it says there are drivers being used) that you would remove, then install... is that it would rebuild the drivers on the current kernel.

---

### Post by steve181 on 2015-01-03
Ok I am in there I attached a picture, it's telling me no proprietary drivers are in use and that amd/anti Richland Radeon HD 8670d is using the recommended driver X.Org X server - Amd/ATI display driver wrapper from x-server-org-video-ati(open source and tested)

its giving me the option to switch it to using video driver for the amd graphics accelerator from fglrx or fglrx-updates

---

### Post by MAFoElffen on 2015-01-03
As another Radeon (and nVidia) user to another... you will be much happier with the flgrx proprietary drivers. The opensourced drivers from Xorg are very basic and lower "featured."

---

### Post by steve181 on 2015-01-04
Thanks you have been a great help, can you tell me why a clean installation of 14.04 gives me 3 separate boot options? The two labeled ubuntu are UEFI options on my main screen.

---

### Post by Dennis N on 2015-01-04
You are looking at the UEFI boot manager. One of those (probably the first one) will go to the grub menu, or boot directly to Ubuntu if its the only OS. Sonetimes, one or more of these don't work. If you do nothing on startup, the boot manager screen shouldn't show, and it will boot to the first option. Your two Ubuntu options may be for secure boot and no secure boot - cant tell without seeing the boot loader each goes to.

---

### Post by steve181 on 2015-01-04
I actually can't get anything to work, now when I try to load fail safe graphics mode I have no mouse and can't get passed the first window warning me I'm in low graphics mode, what if I format disk, load ubuntu 13. Remove the AMD drivers and then upgrade to 14, pressing the left shift key isn't doing anything I'm still going to black screen. Can't even get into fail safe graphic mode.. Thanks again for all the help

---

### Post by steve181 on 2015-01-04
> **Dennis N said:**
> You are looking at the UEFI boot manager. One of those (probably the first one) will go to the grub menu, or boot directly to Ubuntu if its the only OS. Sonetimes, one or more of these don't work. If you do nothing on startup, the boot manager screen shouldn't show, and it will boot to the first option. Your two Ubuntu options may be for secure boot and no secure boot - cant tell without seeing the boot loader each goes to.


The one actually goes to grub rescue>. The first 2 are just going to a black screen..

---

### Post by steve181 on 2015-01-06
I actually got it, I was able to access the grub menu, but somehow got a version to load from there, I switched the drivers and everything is working great now, just installed gns3 and everything been going great, thanks for all the help guys

---

### Post by MAFoElffen on 2015-01-06
Good Job... Please use the link on the upper right of this page "Thread Tools" > "Mark thread as Solved"

---

### Post by steve181 on 2015-01-10
Thanks...will do,  Want to learn as much as I can about Linux, Been using Kali too from a live usb stick but I may try to install it next to windows on my new laptop.... Thanks for all your help

---

