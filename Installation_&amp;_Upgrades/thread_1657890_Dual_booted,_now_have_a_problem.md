---
title: "Dual booted, now have a problem"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by Tayashlor on 2011-01-01
okay, so here's what i've got myself into. 

i have an acer aspire one netbook with windows xp. no optical drive.

tonight i repartitioned my hdd, and installed ubuntu 10.10 netbook via usb. installed fine, but i realized i did the partition wrong while installing. 
so, i restart to windows, use my partition manager, delete the ubuntu partition, and then restart so the program will work. 
restart again, to reinstall ubuntu, and now i get 

error: no such partition
grub rescue> 

it will not let me back onto windows, nor will it boot to the usb drive again. 
i have no idea what to do. 

please help. thanks in advance.

---

### Post by foxmulder881 on 2011-01-01
Does it have a Windows Recovery Partition or other similar hidden partition on the drive?

---

### Post by Tayashlor on 2011-01-01
not that i am aware of. 
i don't mind to loose the windows side. i would prefer not to, but there is nothing on the computer that isnt already backed up. 
i also have a good windows disk/iso, but i dont know how/if there is a way to install via usb.

---

### Post by drs305 on 2011-01-01
If you have a LiveCD/USB you can boot to the Ubuntu desktop and restore the Windows bootloader by running these commands. Don't worry about the messages regarding lilo - run only the two commands and then reboot. 

The commands will point the MBR to the partition with the boot flag so Windows will boot. The commands assume Windows is on the sda drive.

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

---

### Post by Tayashlor on 2011-01-01
> **drs305 said:**
> If you have a LiveCD/USB you can boot to the Ubuntu desktop and restore the Windows bootloader by running these commands. Don't worry about the messages regarding lilo - run only the two commands and then reboot. 

The commands will point the MBR to the partition with the boot flag so Windows will boot. The commands assume Windows is on the sda drive.

```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```


after entering
sudo apt-get install lilo

i got

unknown command 'sudo'
grub rescue>

---

### Post by drs305 on 2011-01-01
> **Tayashlor said:**
> after entering
sudo apt-get install lilo

i got

unknown command 'sudo'
grub rescue>


These commands must be run after booting a LiveCD. You can't run them from the grub rescue prompt.

However, if you are at the grub rescue prompt and know the partition on which Ubuntu might be installed, run the following to see if you can locate the grub files:

```
ls  # finds the known partitions
ls (hdX,Y)/boot/grub  # Can you find grub.cfg?  Example: ls (hd0,5)/boot/grub
# If you find it:
configfile (hdX,Y)/boot/grub/grub.cfg
```

But really, your best option is to concentrate on restoring Windows via the LiveCD and lilo install.

---

### Post by Tayashlor on 2011-01-01
> **drs305 said:**
> These commands must be run after booting a LiveCD. You can't run them from the grub rescue prompt.

However, if you are at the grub rescue prompt and know the partition on which Ubuntu might be installed, run the following to see if you can locate the grub files:

```
ls  # finds the known partitions
ls (hdX,Y)/boot/grub  # Can you find grub.cfg?  Example: ls (hd0,5)/boot/grub
# If you find it:
configfile (hdX,Y)/boot/grub/grub.cfg
```But really, your best option is to concentrate on restoring Windows via the LiveCD and lilo install.

the partition that ubuntu was on is gone. i deleted it on the windows side using easeus, and i also cannot currently boot the the live usb. it keeps taking me back to 

grub rescue>

---

### Post by Tayashlor on 2011-01-01
when i hard reboot with the linux live in the usb it comes up

SYSLINUX 4.02 2010-07-21 EDD Copyright (c) 1994-2010 H. Peter Anvin et al

then stops. the light on my drive stops blinking and nothing happens.

if i hard beboot again, it takes me back to the prompt

the only other thing i can access is f2 settings

---

### Post by drs305 on 2011-01-01
> **Tayashlor said:**
> the partition that ubuntu was on is gone. i deleted it on the windows side using easeus, and i also cannot currently boot the the live usb. it keeps taking me back to 

grub rescue>

Are you sure your BIOS is booting the Live USB first? You might have to go into BIOS to make sure. If it's a USB drive that hasn't been written to it should boot if looked at first.

---

### Post by Tayashlor on 2011-01-01
right now my boot list is:

usb hdd : hp v125w
usb cdrom:
ideo : st9250410as
usb fdd:
ide1:
network boot: atheros boot agent

---

### Post by Tayashlor on 2011-01-01
okay, after going into my boot list again, i am now loaded to the usb live

---

