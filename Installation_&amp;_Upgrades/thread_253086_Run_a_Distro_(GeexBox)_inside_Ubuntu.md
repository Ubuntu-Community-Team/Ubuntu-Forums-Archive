---
title: "Run a Distro (GeexBox) inside Ubuntu?"
date: 2006-09-07
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2006-09-07
I am a big fan of Geexbox, the live CD Media Center, which can also be installed to hard drive, on a separate partition if you like.

A guy on the Geexbox forum has been able to dual boot geexbox and XP from the same partition by doing the hard drive install of geexbox to a USB key, then copying all the files into a directory on XP, and loading the kernel through the M$ boot screen.

I had a shot at doing the same on Ubuntu, writing a new line in grub menu.lst, pointing to the kernel entries for geexbox. The boot process starts but fails at stage 2.

Anyone done anything similar, with success?

---

### Post by taurus on 2006-09-07
You can always try running it thru VMware or qemu!!!

---

### Post by Jose Catre-Vandis on 2006-09-08
> **taurus said:**
> You can always try running it thru VMware or qemu!!!

Yes, can do that already, it was the challenge of getting GeexBox running from Ubuntu grub that I was after.

---

### Post by Jose Catre-Vandis on 2006-09-13
OK, figured this one out, but this applies to GeexBox only!

In Ubuntu, make a copy of your /boot/grub/menu.lst

Reboot PC with GeexBox CD

At the boot screen, type install

Follow installation prompts but DO NOT create new drive / format drive with cfdisk, just select your main partition and QUIT

Geexbox will then copy files over and install GRUB. This will overwrite your Ubuntu grub and not find your Ubuntu installation (because it is on the same partition!)

You will then reboot into GeexBox. Ta da.

Now to get Ubuntu back. Boot with your live CD.
Open terminal and type "sudo fdisk -l"
This will show you where your main partition is.
Then type "sudo mkdir /mnt/gxbx
Then type "sudo mount -t ext3 /dev/hda1 /mnt/gxbx"  (hda1 is my main partition)
Then type "sudo nautilus" and browse to /boot/grub and open menu.lst for editing
Also open your backed up menu.lst

Copy across your ubuntu menu.lst entry and save. Mine looks something like this:
```
default  0
timeout  5
color cyan/blue white/blue
splashimage=(hd0,0)/boot/grub/grub-splash.xpm.gz

title	GeeXboX
root	(hd0,0)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=hda1 splash=silent vga=792 video=vesafb:ywrap,mtrr
initrd  /initrd.gz
boot

title	GeeXboX (debug)
root	(hd0,0)
kernel	/vmlinuz root=/dev/ram0 rw init=linuxrc boot=hda1 splash=0 vga=792 video=vesafb:ywrap,mtrr debugging
initrd  /initrd.gz
boot

title	Ubuntu
root	(hd0,0)
kernel	/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash=0 
initrd  /boot/initrd.img-2.6.15-23-386
boot
```

Reboot and you will find the Ubuntu entry in the Geexbox boot list, and it will boot.

Not sure what will happen when we have the next kernel upgrade :-)

Why the heck am I doing this? Well it will speed up the customisation of GeexBox because all the config files are available to edit, and the install can access all the hardware (DVB card etc), which I cannot do using vmware.

---

### Post by dragonflyseven on 2007-03-07
Hey, thanks! I was looking for this exact thing a few days ago. I ended up accidentally reformatting my partition, so I gave up. Now I can try again.

---

### Post by Triptol on 2008-03-30
Wouldn't really recommend this option, since both distros share the same directory structure. You might be ruining your Ubuntu installation as soon as you install geexbox.

IMHO the better solution is to install geexbox on a USB key. They cost close to nothing nowadays.

---

### Post by Jose Catre-Vandis on 2008-03-31
> **Triptol said:**
> Wouldn't really recommend this option, since both distros share the same directory structure. You might be ruining your Ubuntu installation as soon as you install geexbox.

IMHO the better solution is to install geexbox on a USB key. They cost close to nothing nowadays.

This is not true.Geexbox runs everything from it's own directory, and anyway it boots into ram so doesn't use anything on the disk other than what is in its own directory. Try it, you'll see :)

As I said the whole point was to have Geexbox installed on the hard drive, with easy access (via booting with Ubuntu) to edit configuration files etc. plus I don't have to plug in a USB key or insert a CD. The only thing that you do change is that you use the Geexbox grub (stored inside the GeexBox directory, again :)) instead of the ubuntu grub.

I can't wait until V.2 comes out :)

---

