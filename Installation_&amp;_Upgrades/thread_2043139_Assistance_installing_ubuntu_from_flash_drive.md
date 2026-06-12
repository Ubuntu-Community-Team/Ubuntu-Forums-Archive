---
title: "Assistance installing ubuntu from flash drive"
date: 2012-08-15
forum: Installation &amp; Upgrades
---

### Post by madcow2001 on 2012-08-15
I am running windows 7 64 bit, and wanted to try out linux. I downloaded Ubuntu 12.04 desktop, then downloaded the USB installer mentioned on [http://www.ubuntu.com/download/help/...ick-on-windows](http://www.ubuntu.com/download/help/...ick-on-windows) . I followed the directions, and installed the ISO onto the flash drive.

I rebooted my machine, and booted from USB. I tried to run linux from the flash drive, then got a lot of text. Eventually, it stopped, and it kept repeating this line over and over:

udevd[169]: timeout : killing ' sbin/modprobe -bv pci ..................................... and a lot of jibberish. I have no way of copying the text that I know of, so that's the gist of it.

I tried using a different program to create the flash booter (unetbootin) and tried running from flash drive, and got the same error.

Does anyone have any advice/suggestions on what I can do to fix this?
Thanks!

---

### Post by oldfred on 2012-08-16
What is system and video card/chip?

Often video cards like nVidia need nomodeset. And some very new or very old systems need other boot parameters.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by madcow2001 on 2012-08-16
Ah, didn't know that. I have a Radeon HD 4600 video card, that must be what is throwing it off.  Ill have to check it out later tonight. thanks for the reply!

---

### Post by madcow2001 on 2012-08-16
Ok, I booted from the flash drive into the unetbootin splash screen, and hit tab which brought up the extra info. I cant tell you all of the exact parameters that were there, but it ended in 
"--" I added "pci=noacpi" without the quotes, and still got the same result. So, Im still shopping for answers.

---

