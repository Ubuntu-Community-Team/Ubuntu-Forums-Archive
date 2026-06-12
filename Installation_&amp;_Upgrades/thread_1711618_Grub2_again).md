---
title: "Grub2 again:)"
date: 2011-03-21
forum: Installation &amp; Upgrades
---

### Post by szemy on 2011-03-21
Hi everyone!!!
Well I am back to ubuntu from chrunchbag. Everything ran without a hitch until I decided to delete the old crunchbag partition. I think I might have deleted grub too.So here is what I have now:
A live system from which I am writing from
A primary partition with windows 7 for photoshop
A extended partition with ubuntu and swap(in ubuntu there is the grub directory with some contents in boot)
The questions:
Do I have to set the boot flag for the extended partition or the actual ubuntu partition?
How do I fix things?
I attach some files to make things clear.
Huge thanks for helping
Tamas

ps if I boot normally i get a grub rescue shell...

---

### Post by wilee-nilee on 2011-03-21
You should have loaded grub to the mbr from Ubuntu to avoid this by running from ubuntu.
sudo grub-install /dev/sda
then
sudo update-grub

But in this situation without being in Ubuntu boot the live cd equal to the install and run these two commands.
```
sudo mount /dev/sda5 /mnt
```
then
```
sudo grub-install --root-directory=/mnt /dev/sda
``` 
reboot to Ubuntu and run 
sudo update-grub

Here is the reference for loading grub from a live cd.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

The boot flag needs to be on the windows partition it was on originally for windows to boot from the grub menu and at all. sda1 looks to be a boot partition for windows, so if you remember where you moved it from put it back there.

---

### Post by szemy on 2011-03-22
Thank you very much! Solved in no time:)
By the way do you know how I can enable scroll on my touchpad?
It seems that
```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

is not recognized as a trackpad according to this guide: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Thank you so much!

---

### Post by wilee-nilee on 2011-03-22
> **szemy said:**
> Thank you very much! Solved in no time:)
By the way do you know how I can enable scroll on my touchpad?
It seems that
```
xinput list
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; PS/2 Generic Mouse                      	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Video Bus                               	id=7	[slave  keyboard (3)]
    &#8627; Power Button                            	id=8	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=9	[slave  keyboard (3)]
    &#8627; Lenovo EasyCamera                       	id=10	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=11	[slave  keyboard (3)]
```

is not recognized as a trackpad according to this guide: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

Thank you so much!

Glad you got into Ubuntu, with  the scrolling I have no idea I turn my pad off and use a mouse, I would start a thread using the actual scrolling problem mentioned in the header.

---

