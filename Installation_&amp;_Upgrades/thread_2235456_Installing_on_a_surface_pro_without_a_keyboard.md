---
title: "Installing on a surface pro without a keyboard"
date: 2014-07-21
forum: Installation &amp; Upgrades
---

### Post by cstrrider2 on 2014-07-21
Hey so I feel like I might be being really dumb here but I recently got a surface pro and I want to dual boot it (that's not why I am dumb).  The hard drive is too small so I want to install ubuntu to a microsd card. The problem is there is only one USB and I don't have one of those fancy cover keyboards and none of my hubs seem to want to work so I need to plug a keyboard and therefore I must boot the live CD from the same micro SD card that I want to install to. Which does not make the installer happy. Is there a way to switch live CD sources from the microsd card to a USB drive from inside the live CD? Or maybe a way to make Ubuntu boot to a livecd without using a keyboard? Or even better can someone point out why I  way overcomplicating this?

---

### Post by thenh813 on 2014-07-21
Here's how you install to the microSD.
 Assuming the Surface Pro has a x86 or x64 CPU and can boot removable media, find a desktop/laptop with the same type CPU (x86 or x64) and UEFI (I do not believe Surface supports normal BIOS). The part about UEFI is the most important as Ubuntu needs to be configured to load from GRUB on UEFI. We are using a desktop/laptop to install Ubuntu as we can use its keyboard, and start the OSK (on screen keyboard) by default once installed for the tablet.

1: Go to the PC, and unplug its internal HDD so you dont accidentally format it instead unless you are ABSOLUTELY SURE you know what you are doing. You also want to remove ALL OTHER MEDIA (flash drives, SD cards) from the computer. once again so you dont accidentally install to the wrong device.

2: Boot the Ubuntu LiveCD/DVD for the architecture desired, x86 WILL WORK on x64 so if your desktop is x86 you can use that. You just wont get the enhancements of x64 (using more than 4GB RAM, enhanced instruction set).

3: Gparted! Open GParted and partition the card as  follows: 500MB EXT2 partition first, all the rest of space to ReiserFS, EXT4, XFS or EXT3 (your choice).

4: Install Ubuntu normally to the SD card from the usual setup process, set the first small partition to mount as /boot, set the second to mount as /.

   5: Wait till the install is finished, set the PC to boot from the SD or the card reader it is in and try it on the PC. It it loads fine, set the on screen keyboard to run at startup, then shut it down and remove the card.

  6: Insert the card into the Surface and configure it to boot from the card, if all went well if will work just fine. 

 If this does not work, I will find out how to install to a  SD from the surface. You almost definitely WILL need a keyboard, USB will be fine. One could install Ubuntu using a ROM image but that would not allow dual booting and would erase Windows.

---

### Post by cstrrider2 on 2014-07-21
Thanks for the Reply,

I appreciate the help but my issue is not that I don't know how to install ubuntu on any computer in general.  Its specifically related to having one USB and no keyboard for the Surface Pro. My pro has a i5 so I know it can run ubuntu x64 (I have gotten it to boot using the microSD I just can't install it) has 1 usb, 1 microSD slot, no surface pro keyboard, and a 64GB SSD (which only has 15gb available so I dont want to partition that away). I have made a bootable USB but I can't get passed GRUB without a keyboard and I don't have any of the the surface keyboards. I was able to boot by making one of the 2 partitions on my MicroSD card ubuntu bootable and plugging in a keyboard, however I can't then install Ubuntu to that microsd card because Its mounted for the installer.  If I had a surface pro keyboard (which connects to a special port and therefore leaves the usb open) or if I could get past grub without needing a keyboard to press enter and could boot from the USB stick (I can use onboard once ubuntu has booted) or I had enough room on the internal SSD (which I don't) I could make this work, but right now I am kind of stuck.

---

### Post by grahammechanical on 2014-07-21
I think the question you should be asking is this: Is it possible to install Ubuntu off of a USB memory stick using the on-screen keyboard?

That is something that I have never tried. If I was going to try this, I would load to the live session desktop and then activate Orca the on-screen keyboard and then active the Install Ubuntu icon from the live session and see what happens. I might try doing that tomorrow. Unless you get in first and tell me it does not work. Would using a mouse count as cheating. :) Not if you have a track pad or touch screen.

Regards.

---

### Post by cstrrider2 on 2014-07-21
I can use the onscreen keyboard everywhere but grub.  I cant make grub boot without a physical keyboard unless someone knows something I dont

---

### Post by grahammechanical on 2014-07-21
There is this post but it does not offer hope.

[http://stackoverflow.com/questions/15419236/adding-touch-sensitivity-to-grub-2-boot-loader](http://stackoverflow.com/questions/15419236/adding-touch-sensitivity-to-grub-2-boot-loader)

And this old forum thread but I am not sure if anything in it is relevant to you.

[http://ubuntuforums.org/showthread.php?t=2183946&page=2](http://ubuntuforums.org/showthread.php?t=2183946&page=2)

Regards.

---

### Post by sp40140 on 2014-07-22
How about using USB Hub? something like.....[http://www.amazon.com/Black-4-Port-High-Speed-USB/dp/B002FFT8Z6/ref=sr_1_6?s=electronics&ie=UTF8&qid=1406050242&sr=1-6&keywords=usbhub](http://www.amazon.com/Black-4-Port-High-Speed-USB/dp/B002FFT8Z6/ref=sr_1_6?s=electronics&ie=UTF8&qid=1406050242&sr=1-6&keywords=usbhub)

---

### Post by cstrrider2 on 2014-07-22
i did try a hub and it didn't work but it might have been broken or something ill give it another shot

---

