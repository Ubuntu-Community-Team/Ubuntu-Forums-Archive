---
title: "Live usb not bootable: “Couldn’t get size: 0x800000000000000e”"
date: 2019-08-09
forum: Installation &amp; Upgrades
---

### Post by larcoscarsa on 2019-08-09
[ubuntu]

Hi guys,

After having build my new pc, I wanted to install ubuntu 18.04 LTS ont it.
So, I made a live usb with the Unetbootin tool.
When I am trying to boot on it, the screen freezes and I am getting this error message:
&#8220;Couldn&#8217;t get size: 0x800000000000000e&#8221;

I do precise that my pc contains the last Nvidia RTX 2080 super (released in July) and the amd Ryzen 3700x. 
I have read that this message could come out from some issues with the graphics drivers so I tried to connect directly my screen to the motherboard HDMI output put the motherboard didn't send any signal to the screen, most probably because my graphic card was connected.
I also read that ryzens 3000 could generate some issues on booting with certains linux distros but that shouldn't concern ubuntu 18.04 LTS  


Here is my build in details:
Motherboard: Asus x570 prime pro
Processor: Ryzen 3700x
Graphics card: Nvidia gigabytes rtx 2080 super
Ram: 16Go
Hard drive: Nvme samsung evo plus 500 Go

I would like to point out that this not my first installation, and that I never got such issues.

What would be the solution: updating the bios, using an other distrbs etc...?

---

### Post by Autodave on 2019-08-12
I did a little research on this.  The only help that I could find seems to be that there is a problem with *Secure Boot *enabled in the BIOS.  You may want to disable that and give it another try.

---

### Post by oldfred on 2019-08-12
Have you updated UEFI? New UEFI for support of Linux just released by vendors.


       AMD UEFI/BIOS update for Ryzen 3000 series
[https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good](https://www.phoronix.com/scan.php?page=news_item&px=Ryzen-3000-BIOS-Update-Good)
ASUS ROG CROSSHAIR VIII HERO WiFi - update supports Ubuntu 19.04
MSI has also put out BIOS updates last week as a "beta" though without explicitly acknowledging the Linux fix.

---

### Post by &amp;wP*!) on 2019-08-14
[Similar problem]("https://ubuntuforums.org/showthread.php?t=2424000&highlight=couldn%27t+size") .
Update the UEFI to the latest from the vendor.
if SecureBoot is off, you can safely ignore the warning.

---

