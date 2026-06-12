---
title: "[SOLVED] Black Screen when booting from LiveCD"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by burgerearl on 2007-11-24
**My problem:**
I'm having trouble that it seems like others have had too. Booting the live CD goes smoothly until the loading bar completes (after the splash menu) and then I get a black screen. This happens both for a normal boot and a "safe graphics mode" boot.

I am able to use Alt+F1 to get a command line. The main solution I've seen on other posts is to manually configure xorg (sudo dpkg-configure xorg-xserver) from that commmand line. I've tried this, however it was already correctly auto-detecting my refresh rates. I tried removing some of the higher resolution options but this didn't help either:

After configuring xorg, if I try "startx" I get an error that x is already running. I was able to use "rm -rf /tmp/.X0-lock" to solve that problem, but "startx" then just gave me a black screen again (still able to return to CL with ALT+F1)

I have tried to run with Ubuntu 7.10 and 7.04, as well as Kubuntu 7.10, all giving the same results.
[B]
My setup:[/B]
AMD Athlon64 3000+
Radeon 9200
1GB Ram
80GB HDD with 50 GB NTFS Partition and 30 GB unformatted partition
I have tried two monitors:
LG L192WS
Old Sony CRT monitor

**My questions:**

[LIST]
[*]Is there something other than refresh rates or resolutions that I should be editing in xorg to get this to work?
[*]Can I install Ubuntu onto my unused partition from the command line and manually edit some files to get a GUI? If so, is it something a complete Linux newbie (me) can handle?
[*]Is there a problem with my graphics card? I've seen the same problem posted by people with the same card, but also from folks with different setups.
[*]What about my monitor? It seems like xorg is correctly autodetecting the settings my monitor needs, so what should I try here?
[/LIST]

Thanks for any help, hopefully by the end of the weekend I can get this running.

---

### Post by Pumalite on 2007-11-24
The Monitor I think you eliminated it as a problem. Your card is ATI; a problem in itself, but shouldn't be a problem for a Live CD with your memory. I think you should try different boot parameters. Here is a guide and a collection of them:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by burgerearl on 2007-11-24
I wasn't completely clear on what you wanted me to try, but I think I did this correctly. I pressed F6 on the options splash screen and entered the additonal parameter(s) after the last parameter that was already there ("quiet splash --"). I tried each parameter individually, as well as all 6 together.

[list]
[*]noapic:  no change

[*]nolapic: error: 
/bin/sh can't access tty; job control turned off
(initramfs) [   70.666725] ata1.00: failed to set xfermode (err_mask=0x40)

the 2nd line repeated twice more with only the number 70.666... changing
Also, after the error, I got what appeared to be a command prompt of "(initramfs)" instead of the usual ubuntu@ubuntu:~$


[*]acpi=off:

Several errors about PnPBios that appeared _before_ the screen with the loading bar, then the same black screen after. Still able to get a normal command prompt with Ctrl Alt F1.

Also, I'm not positive, but when I used ctrl alt del to restart, it looked like it may have killed more processes than usual.

[*]pci=nocpi: no change
[*]pnpbios=off: no change
[*]vga=0x317: higher resolution for the blinking cursor before the black screen and the command prompt after ctrl alt F1, but otherwise no change

Also, the message to remove the CD from tray (after Ctrl Alt Del) was orange instead of blue, which it was the rest of the time. However, it was not responsive after closing the tray and pressing Enter to continue the reboot.

[*]All 6: exactly the same as 0x317, including orange vice blue CD tray message and unresponsiveness.
[/list]

For my general education, is the option screen where I entered these parameters Grub, or something else?

Thanks for the help, although it was unsuccessful. Any further suggestions?

---

### Post by Pumalite on 2007-11-25
Try the Alternate CD.

---

### Post by burgerearl on 2007-11-25
Thanks.

I was able to successfully install using the alternate CD.

Boot happens normally, GRUB worked fine from the Windows MBR. I can boot both Ubuntu and Windows as I would expect.

But I still get a black screen after the ubuntu loading bar. I tried using Ctrl Alt F1 and then "startx" from the command prompt and I got the following error (after using sudo rm -rf /tmp/.X0-lock):

AIGLX: Screen 0 is not DRI Capable


This seems more helpful than other errors I've seen. From what I gathered googling and forum searching, this sounds like it relates to your comment before that having an ATI card would be a problem in itself. Should I start a new thread in another category or is there more help to be had here?

Thanks a lot getting me installed though, here's hoping I can get an Ubuntu GUI to go with it...

---

### Post by Pumalite on 2007-11-25
At the command line:
sudo dpkg-reconfigure xserver-xorg
Choose most defaults
Try 'ati' as the driver
If not, 'vesa' as the driver
Then startx

---

### Post by burgerearl on 2007-11-25
I tried both ati and vesa as options. It was defaulting to vesa, I think that's what it was using before.

using **ati **gave this error:

(WW) Radeon: No matching device section for instance (BusID PCI:1:0:0) found
(WW) Radeon: No matching device section for instance (BusID PCI:1:0:1) found

(EE) No devices detected

Fatal server error: no screens found

XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining

using **vesa**, I heard the ubuntu start sound (first time I've had speakers hooked up, so I don't know if it got that far when I was using the liveCD), but I got the following error:

Aiglx: Screen 0 is not DRI capable

Thanks again.

---

### Post by Pumalite on 2007-11-25
Looks like your Monitor might be a problem. What do you have?

---

### Post by burgerearl on 2007-11-25
I'm currently using an acer AL2216W, which is correctly being autodetected when I configure X. I have another monitor on my desk though, I'll try that one and see if I get different results.

You said before that my ATI card might be a problem, should selecting the ati driver solve that?

---

### Post by Pumalite on 2007-11-25
Vesa is a generic driver that should work with any card. But I suggested earlier to try ati just in case it works.

---

### Post by burgerearl on 2007-11-25
Tried both vesa and ati with another monitor (Philips 170S) and got the exact same results as posted above. 

Since my installation issues are solved and I'm now trying to solve display issues, should I mark this thread solved and start a new thread in "Multimedia & Video"?

---

### Post by Pumalite on 2007-11-25
Good idea. Good luck.

---

