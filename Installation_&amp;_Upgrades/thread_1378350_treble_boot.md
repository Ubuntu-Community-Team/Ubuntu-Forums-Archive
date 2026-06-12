---
title: "treble boot"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by Masmajou on 2010-01-11
First - I am new to Ubuntu, and already love it.

I have installed Ubuntu 9.10 on my Vista disk as dual boot - and works well ... but I have another drive with XP installed and want to have the option to boot to Ubuntu / Vista / XP (I have reasons to need all three!!).
Is there a way this can be acheived?

---

### Post by underquark on 2010-01-11
Easiest way - since you say XP is on another drive - is to go into BIOS (press F2 or whichever key it is on your computer) and boot from the XP drive when you need to.  Yes, you can edit Grub etc. but why risk it?

---

### Post by oldfred on 2010-01-11
All grub does is jump into the windows partition and turn over booting to the windows boot. 

If your hard drive was separate from the Vista install then the installs were not combined and you should be able to directly boot winXP.

It may be as simple as 

sudo update-grub

If that does not work it is probably that the added drive is not yet recognized in grub. Look at /boot/grub/device.map, it should show two drives. You may be able to manually add the second drive or:

I have not done it but:

sudo grub-mkdevicemap

or
 it will create a new device map if it does not see one.
cd /boot/grub
sudo mv device.map device.map.bu
sudo update-grub

---

### Post by Masmajou on 2010-01-11
Thanks - I went for updating the grub.
It works fine now, thanks for your help.

---

