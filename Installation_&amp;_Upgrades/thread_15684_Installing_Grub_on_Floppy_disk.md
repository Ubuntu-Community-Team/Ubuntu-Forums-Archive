---
title: "Installing Grub on Floppy disk"
date: 2005-02-16
forum: Installation &amp; Upgrades
---

### Post by Highlag on 2005-02-16
Hi!

I would like to install Ubuntu on free space on my second disk which I use for backup purposes.  I do not wish to put anything on my primary disk which is also boot disk.

I have already tried to install but I was not able to change Grub installation point.  Every time I try Grub install itself on MBR of my second disk, so I never managed to boot to Ubuntu.  Can I install grub somehow on floppy or better on CD?  :roll: 

If this can be done, can someone instruct me how can I do this? I am a newbie regarding Linux.


My primary disk is on SATA, secondary is ATA100.

---

### Post by m4ng0 on 2005-02-16
If you want to boot from floppy, you can:

1) create a proper MBR on a floppy:
check that your /boot/grub/menu.lst file is correct, then type:

sudo grub

which should answer with its prompt "grub>"; then you have to do this:

grub> find /boot/grub/stage1

which tells you in which partition is your boot directory, e.g. (hd0,1).
Now you tell grub that it has to use that partition as its root partition:

grub> root (hd?,?)

where you have to replace ? with correct numbers. Now insert a floppy and type:

grub> setup (fd0)

That's all:

grub> quit

Now you can shut down, set bios to boot from floppy, and... enjoy!

2) create a GRUB boot floppy which doesn't know anything about your menu.lst:
insert a floppy and type:

cd /boot/grub
dd if=stage1 of=/dev/fd0 bs=512 count=1
dd if=stage2 of=/dev/fd0 bs=512 seek=1

Now you have a GRUB boot floppy, very useful for debugging... but when you
boot it, you have to supply all the informations usually located in menu.lst
(set: root, kernel, initrd and then you can boot).

3) If you have problems installing grub on your SATA hard disk, check
/boot/grub/device.map because (at least I think so) SATA drives don't
follow /dev/hd? naming rules... but I don't hava SATA, so I'm not sure.

---

### Post by Highlag on 2005-02-16
Thank you for reply, but unfortunately I have another question.

Can I do all this stuff from Ubuntu setup ?  Because I never booted to Ubuntu before, and all commands you sugested are Linux commands?

---

### Post by m4ng0 on 2005-02-16
I know this is not a good solution but... can you choose (from BIOS) which hard drive should be booted? If you manage to boot from the second disk (whose MBR was written by Grub) you can complete your installation and create the boot floppy as I told you in the previous post. Once you have created the boot floppy, you can restore BIOS so that it boots from the first disk and use the floppy when you want to boot Linux. It could be a temporary solution, so you can investigate why grub does not install on your first disk.

---

### Post by Highlag on 2005-02-17
Thx for your effort. I did as you said, but I am cursed or something  :roll: 
X windows failed to load.....

---

### Post by m4ng0 on 2005-02-17
You can try:
sudo dpkg-reconfigure xserver-xfree86
and if this doesn't work, post relevant parts of
/var/log/XFree86.0.log

---

