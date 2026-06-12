---
title: "Grub rescue mode: how to avoid?"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by Tactical Fart on 2012-04-27
I'm only putting this here because I think this may fall under the installation category. Mods, feel free to move it.

Anyway, I keep getting getting rescue mode every time I boot. I can always use the instructions [here]("https://help.ubuntu.com/community/Grub2#Rescue_Mode_.28.27.27grub_rescue.3E.27.27.29_Booting") and boot, but like the guide says, these changes are not persistent and must be repeated next time the system starts. I have also tried the "sudo grub-install /dev/sdX" command that the guide suggests. It did... stuff, but didn't fix the problem. Also "sudo fdisk -l /dev/sdb", if i'm reading it right, confirms that the installation partition has the boot flag.

I'm rather sure that it is a problem with configuration or I couldn't boot at all. Any Ideas?

---

### Post by garvinrick4 on 2012-04-27
Use Live CD (UBuntu install CD using Try Ubuntu) open a terminal:
```
sudo fdisk -l
``` (lower case L)
Find your linux install you want to use for booting:
I will use sda5 for this [COLOR=Red]use your own:[/COLOR]
```
sudo mount /dev/sda5 /mnt
``````
sudo grub-install --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```Reboot

---

### Post by Tactical Fart on 2012-04-28
I would have tried sooner, but got buried under other stuff to do.

Unfortunately, it didn't work. Here's the entire error (same as before, not cut/pasted).

```
GRUB loading.
Welcome to GRUB!

error: unknown filesystem.
Entering rescue mode...
grub rescue> _ 
```

---

### Post by darkod on 2012-04-28
It clearly complains about some unknown filesystem. Are you using any rare or unsupported FS?

What does parted say?
sudo parted /dev/sdb print all

---

### Post by Tactical Fart on 2012-04-28
darkod, I think i wasted your time.

The output from the command you gave me revealed that my other sata drive, /dev/sda (used ony for storage) had a partition with the boot flag enabled but /dev/sdb is the one with a bootable partition. Since this is a custom built machine, I tried unplugging the sata cables from the drives (while the machine was powered off) and switching them, so that the bootable drive would become /dev/sda and thus first. 

While writing this response I realized that I might have gotten away with configuring my bios, but whatevs.

garvinrick4, I think your suggestion didn't work because the system was still looking in /dev/sda to boot.

Thank you eveyone for your help. This is truly one of the best forums on the internet.
:guitar:

---

### Post by darkod on 2012-04-28
Yeah, you could have just selected in BIOS to boot from the other disk as first option. Common confusion with multiple disks. :)

Please mark the thread as Solved. You can do that in Thread Tools above the first post.

---

### Post by shankarc on 2013-02-18
im unable to login still getting the same message
 
Unfortunately, it didn't work. Here's the entire error (same as before, not cut/pasted).
 
[CODE]GRUB loading.
Welcome to GRUB!
 
error: unknown filesystem.
Entering rescue mode...
grub rescue> _

---

