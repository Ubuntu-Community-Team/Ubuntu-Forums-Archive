---
title: "System halts on boot"
date: 2011-11-09
forum: Installation &amp; Upgrades
---

### Post by crazy bird on 2011-11-09
Hi,
I&#8217;ve tried to install Xubuntu 11.10 on my system. The installation went smoothly till I had to reboot my system in order to finalize the installation. Booting the BIOS gave no problems, I saw the boot screen of Xubuntu and after a few seconds it started blinking and then I saw a black screen with those &#8220;command lines&#8221; (or boot sequence or how-do-you-call it) and then my system halted. Nothing happened except the cursosr whoch was blinking. No hard disc activity, nothing. I let the system  that way for a half an hour and still nothing happened.
My system:
Asus P5KPL-AM Motherboard
Intel Core2 Quad Processor Q8200 (4M Cache, 2.33 GHz, 1333 MHz FSB)
NVidia _**GeForce 9500 GT**_
4 Gigabyte memory
1 TB HDD
500 Gb HDD
1.5 TB external USB Disc
HP ePhotosmart B110a
Does anyone know what my problem might be? And is there a solution for my problem?
Many thanks in advance!

---

### Post by sideburns on 2011-11-09
What is the last line of the boot sequence that gets to the screen before it hangs?  If it ends with [OK] that will mean that it's hanging on the next item, and somebody might know that that is.  And, did any of the items listed fail?  It might be significant.

---

### Post by MAFoElffen on 2011-11-09
> **crazy bird said:**
> Hi,
I’ve tried to install Xubuntu 11.10 on my system. The installation went smoothly till I had to reboot my system in order to finalize the installation. Booting the BIOS gave no problems, I saw the boot screen of Xubuntu and after a few seconds it started blinking and then I saw a black screen with those “command lines” (or boot sequence or how-do-you-call it) and then my system halted. Nothing happened except the cursosr whoch was blinking. No hard disc activity, nothing. I let the system  that way for a half an hour and still nothing happened.
My system:
Asus P5KPL-AM Motherboard
Intel Core2 Quad Processor Q8200 (4M Cache, 2.33 GHz, 1333 MHz FSB)
NVidia Geforce 9800GT
4 Gigabyte memory
1 TB HDD
500 Gb HDD
1.5 TB external USB Disc
HP ePhotosmart B110a
Does anyone know what my problem might be? And is there a solution for my problem?
Many thanks in advance!
LOL... Respect to Post #2, but since it's a new install and you have NVidia, the message on the screen is most likely "chacking the battery state" thru the "system 5 compatability" message... Meaning the video driver it not loading.  On a fresh install w/ nvidia, that's because you haven't install it yet:
Reboot. > On Boot, hold down the shift key. > When the Grub Menu comes up, press "e" to enter an edit menu. > Arrow down to the line that starts with "linux." > Arrow right to after where it says "quiet splash" and before it says "vt.handoff=7" > Insert the text "nomodeset" > Press <cntrl><x> to boot with those options.

It should boot to the desktop.  When it does, install your nvidia-current video drivers.

Tell me how it goes.

---

### Post by sideburns on 2011-11-09
I wish you had popped in when my sister's Ubuntu box was hanging at exactly that point.  It turns out that her computer's auxiliary video card (unused) was bad and removing it got things working again.

---

### Post by crazy bird on 2011-11-13
Just discovered a mistake, i don't have the Geforce 9800GT card but the NVidia GeForce 9500 GT videocard! My apologies!

---

### Post by hoppings on 2011-11-13
Hi, I have a similar problem to crazy bird.
I installed Xubuntu on a Sony Vaio VGN-T1XP little laptop with 1GB memory, alonside XP.
I briefly get the Xubuntu splash logo then blank screen forever.

As per MAFoElffen's suggestion I tried going into edit mode on boot as per suggestion and adding "nomodeset" but no joy with it.
There was no "vt.handoff=7" anywhere in the box.
This is how the text stands at the moment:-

GNU GRUB  version 1.98-lubuntu10
recordfail
insmod ext2
set root='(hd0,5) '
search --no-floppy --fs-uuid --set c23738cb-e57d-9176-5a64e3945\676
linux /boot/vmlinuz-2.632-28-generic root=UUID=c23738cb-e57d-438a-9\176-5a64e3945676 ro  quiet splash
initrd /boot/initrd.img-2.6.32-28-generic

There may be a typing error or two.

Can you offer any suggestions please.

---

### Post by scratcholam,an on 2011-12-02
I had a similar problem a couple of weeks ago, (about the time this thread was started)
 I don't remember exactly how I fixed it, but here's what I remember.

I think if you press F1,   ALT+F1 or   CTRL+ALT+F1 it will open a terminal.
From there you should be able to log in.

Then type ```
startx
``` or maybe```
 startxfce
```Hopefully that will get you going, but you will have to do that every boot.

There were a couple of files that needed editing to do it automatically, but I have no clue as to what they are.

I think one file would automatically log you into tty1 and
The other would start the xfce-desktop after the login into tty1.

Good Luck, I know I need it.

---

