---
title: "Nvidia 8800GTS on 10.4"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by Scott Sherman on 2010-05-12
Hello there,
 
I'm just wondering whether anybody has had any issues with drivers for a nvidia 8800gts graphics card when installing Ubuntu 10.4? 
 
There are 3 generic drivers available on there but neither seem to work/will not activate?
 
Cheers

---

### Post by oldfred on 2010-05-12
I have a 9600gt which I think is really the same (marketing)

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

After I installed nvidia driver (default newest from pop up) then it has worked without issue.

Other info:
Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

---

### Post by davepimp00 on 2010-05-25
> **oldfred said:**
> I have a 9600gt which I think is really the same (marketing)

I had to do this:
boot from the cd, press F6 and then select the Nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot

After I installed nvidia driver (default newest from pop up) then it has worked without issue.

Other info:
Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
# Nvidia (this should revert you to using -nv or -vesa):
echo options nouveau modeset=0 > /etc/modprobe.d/nouveau-kms.conf

Sorry im new but i have a question, when you say "press e on getting the GRUB bootloader."  what does this actually mean?

---

### Post by oldfred on 2010-05-25
When you boot the grub menu comes up and normally gives you 10 sec before booting the default menu entry. Once of the choices is to edit a menu entry before booting, very good for testing alternatives or fixing problems to get into system and make permanent fixes.

---

### Post by JohnHeikkila on 2010-09-09
Grub 2: Hold SHIFT when the white mark is blinking on the black background
Grub legacy: Press ESC when it says you can

---

### Post by DemanRisu on 2010-09-09
afaik, the 8800GTS is more powerful than the 9600. I'd say it's more at the power level of a 9800GTX. The 9xxx line was just a rehash of the previous generation's technology with smaller chips.

---

### Post by cascade9 on 2010-09-09
> **oldfred said:**
> I have a 9600gt which I think is really the same (marketing)

Nope, the 9600GT has a different chip, a lot less power and 128bit interface, not the 256/320bit interface like the 8800 series cards.

> **DemanRisu said:**
> afaik, the 8800GTS is more powerful than the 9600. I'd say it's more at the power level of a 9800GTX. The 9xxx line was just a rehash of the previous generation's technology with smaller chips.

Depends on which 8800GTS. There were 2 versions- G80 (98:48:20, 513MHz core, 1188Mhz sharders, 1584MHz memory, 320bit interface, in 320 and 640MB versions) and G92 (128:64:16, 650Mhz core, 1625Mhz sharders, 1940Mhz memory, 256bit interface, 512MB only). 

9800GTX is a chunk faster than the 8800GTS G92 (128:64:16, 675Mhz core, 1688Mhz shaders, 2200Mhz memory) but its probabl the closest of the 9800 seires to the (G92) 8800GTS. 

BTW, only the 9800 series cards was a 'rehash'- the lower level cards were new chips. Also, not all the 9800s were the smaller 55nm process, there are 65nm process 9800s. You have to get a 9800 'green', 9800GTX+ or a GTS250 (g92 again!) to know you are getting the smaller 55nm process.

---

