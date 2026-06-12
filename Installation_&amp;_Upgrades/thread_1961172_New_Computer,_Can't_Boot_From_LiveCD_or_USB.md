---
title: "New Computer, Can't Boot From LiveCD or USB"
date: 2012-04-18
forum: Installation &amp; Upgrades
---

### Post by Jackelope King on 2012-04-18
Hey all, I'm trying to get my new computer up and running, and it's been giving me agita.

When trying to boot from the LiveCD, this is where I can get to, after which point the boot sequence simply stops and hangs indefinitely:
[IMG]https://lh3.googleusercontent.com/-j9iyrkrPiGI/T489uhECOFI/AAAAAAAAAXY/odaDelgz87Q/s773/IMG_20120418_181828.jpg[/IMG]

Suspecting the problem is the USB ports mounted on the mobo (ASUS P8z68-VLE), I disconnected my USB keyboard and mouse and plugged in an old PS/2 keyboard. This is the result:
[IMG]https://lh3.googleusercontent.com/-RdzNuYL-ux4/T49EuRfjdBI/AAAAAAAAAXk/_wFDggmQohY/s773/IMG_20120418_184819.jpg[/IMG]

Am I correct in assuming that this is a problem with the USB hub? If so, does anyone have any ideas on how I can fix this? If not, any ideas on where else I can check?

Thanks, folks.

---

### Post by wojox on 2012-04-18
Which version of Ubuntu?

Bad burn maybe.

---

### Post by Jackelope King on 2012-04-18
> **wojox said:**
> Which version of Ubuntu?

Bad burn maybe.

11.10. I've tried two different LiveCDs (And have successfully booted from it on my older laptop) and the USB. No luck yet.

---

### Post by wojox on 2012-04-18
> **Jackelope King said:**
> 11.10. I've tried two different LiveCDs (And have successfully booted from it on my older laptop) and the USB. No luck yet.

Ahhh, good it works on another computer. What about a BIOS setting?

---

### Post by Jackelope King on 2012-04-18
Alright, looks like progress is being made. Removed the video card (a really nice EVGA GTX 560ti) and I can boot with the onboard video.

---

### Post by MonkeyPaw on 2012-04-18
> **Jackelope King said:**
> Alright, looks like progress is being made. Removed the video card (a really nice EVGA GTX 560ti) and I can boot with the onboard video.

I was about to suggest a hardware issue. You might check the BIOS to see if your integrated graphics are set to disable when a graphics card is installed. There's a setting to determine what graphics device gets priority on boot, and you might try setting it to the PCIe/Peg if your 560Ti is installed.

---

### Post by oldfred on 2012-04-18
My nVidia is older but all nVidias seem to need nomodeset.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by mastablasta on 2012-04-19
after booting with nomodeset you might be able to install proprietary drivers (not really needed on live CD)  which should solve nomodeset "issue".

---

