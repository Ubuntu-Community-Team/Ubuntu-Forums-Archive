---
title: "lucid upgrade hard fail"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by Dreen on 2010-05-17
I am reposting this here from general help where i got no help.

I upgraded to 10.04 and cannot boot my system, even in recovery mode. No errors are shown, only some random color noise at the top of screen. Starting on older kernel didn't help. I managed to load a 10.04 livecd (not without issues) and can access my linux partition. I restored the xorg.conf backup made by the upgrade, but that didn't help, still random color noise. Where can I look for clues as to whats wrong? Before 9.10 was functioning perfectly.

My computer is Asus 1201N: [http://uk.asus.com/product.aspx?P_ID=sZ0sI6WqjnCHGFta](http://uk.asus.com/product.aspx?P_ID=sZ0sI6WqjnCHGFta)

---

### Post by Dreen on 2010-05-18
bump

---

### Post by jetsam on 2010-05-18
You're in scary bad graphics land, so wait for other people's opinions.  You should probably just shut the system down.  I think your graphics card has gone south, but it might just be software.  

Does asus have a support forum?  They might be more familiar with the specific symptoms.

---

### Post by oldfred on 2010-05-18
I have nvidia on my desktop:

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.

if you've got an intel graphics card, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes) 

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

