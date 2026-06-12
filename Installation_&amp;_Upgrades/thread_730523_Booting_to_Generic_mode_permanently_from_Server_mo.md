---
title: "Booting to Generic mode permanently from Server mode?"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by badspell68 on 2008-03-21
How do I boot permanently to Generic mode instead of Server mode mode? If I switch it by hitting the ESC key on boot and choose Generic it switches back to Server mode the next time I startup.

:confused:

---

### Post by badspell68 on 2008-03-25
FOUND HOW TO DO IT:


2. Making Boot Parameter Changes Permanent

Assuming that you booted with a new or changed parameter and would now like to make this a more permanent change, you need to edit the file that contains these settings. This file (/boot/grub/menu.lst) is owned by root and, therefore, requires root privileges to edit. There are a number of ways to do this depending on your editor of choice. For me
sudo vi /boot/grub/menu.lst
works. If you are not familiar with vi, then it might by something along the lines of
gksudo gedit /boot/grub/menu.lst
will edit this file in the Ubuntu gedit graphical text editor.

Now, there are two flavours of permanent to consider. The first is to make the change survive reboots, the second is to survive an upgrade.
2.1 Making a change survive reboots

Find the section shown below. The details will vary depending on which kernel(s) are installed on your machine.
## ## End Default Options ##

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault
Add your parameters to the end of the line starting with "kernel...". This should be the same line that you would edit in the temporary change scenario above. Save the file and the change will survive a reboot.

2.2 Making a change survive upgrades

Depending on how frequently you upgrade your system, you might find that when a new kernel is installed, or grub is upgraded (there may be other scenarios), the /boot/grub/menu.lst file may be replaced by a newer version, or a new line might be added for the new kernel. In this case, your "permanent" changes might be as permanent as you thought.

The best way to address this is to change the "#kopt..." line in /boot/grub/menu.lst. Note that the line is not commented out, even though it starts with a "#". See the excerpt below.
### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro
Add the parameter changes to the end of the line "#kopt...". These parameters will then be automatically added to any new kernel entries and should also survive an upgrade of grub.
One last point: When installing Ubuntu, the very first screen you get to when booting with the install CD has an option to set boot parameters for your system. If you know ahead of time of boot parameters that need to be set to make your graphics card work, for example, then setting them here will not only make your installation much smoother, but they will also get added as default options, as in (2.2) above.

---

