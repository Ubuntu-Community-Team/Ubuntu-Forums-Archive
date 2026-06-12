---
title: "howto fix defect /boot partition using grub?"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by phibuntu on 2007-04-03
Hello everybody

I "killed" my boot-partition. (I wanted to install a boot-loader on an external USB-drive and "grub-install /dev/sdb" killed my harddisk boot-loader.)

At the moment, when I start my computer I get the following prompt:

```

    Minimal BSAH-like line editing is supported.   For
    the first word, TAB lists possible command
    completions. Anywhere else TAB lists the possible
    completions of a device/filenam. ]

grub>   

```

Using 
```

grub> root (hd0, 0)
grub> setup (hd0)

```
leads to some checkings and some Runnings, with all exit and succeeded:
```

  ... stage1, stage2, e2fs_stage1_5 ... -> exist
  embed ... e2fs_stage1_5 (hd0) -> succed
  install ... stage1 (hd0) succeed

```

What next?
I get the possible commands, but how to fix grub, so that it boots again?
I am either able to boot, nor to fix the boot-loader, so that it starts again.

Fortunatelly I have a separate partition called "/boot" (/dev/sda1)
the root partition ("/") is on /dev/sda3

I manage to start the "live-system" (edgy) and I am able to mount the above mentioned partitions. Will this help?

Thanks in advance for every hint.

---

### Post by 1/0 on 2007-04-03
You could chroot into the system if you have mounted first / and then /boot.

```
chroot /mount/point/for/ /bin/bash
```

Then:

```

sudo grub
root(hdx,y)
setup (hdx)
quit

```

Change x and y to your case. Hopefully that'll install GRUB. Then you can check the config:

```
nano -w /boot/grub/menu.lst
```

You should have something like this:

```

timeout         5
title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash  rootflags=data=writeback
initrd          /boot/initrd.img-2.6.17-10-generic


```

---

### Post by phibuntu on 2007-04-03
Thanks 1/0

you saved my day.

I did what you posted, but after the reboot, I still got the prompt.
So I entered "kernel ... root=..." and "initrd ..." and "boot" by hand.
After changing the menu.lst (which was corrupt and did not contain an initrd-entry)
the system was alive again.

:)

and more: I (an old linuxer using lilo since years) learnd something about grub!

---

### Post by 1/0 on 2007-04-03
Glad to help! GRUB can be tricky to deal with, especially when one is used to LILO. (I have't used LILO since Red Hat 5.2 or something like that).

---

### Post by phibuntu on 2007-04-17
I have still not finished my 4GB usb-stick ubuntu project.
But most things I wanted work now.


I installed Ubuntu on a 4GB USB Stick.
First, I killed my Boot Block on the internal Hardware. So beware. You will find a solution above.

Then I was not able to boot the stick on different PCs.
Problems

1. Some PCs are not able to boot from USB sticks. (no solution yet).
2. Some PCs have the usb drive at /dev/sda, other have it at /dev/sdb.
    Solution: I copied the /boot/grub/menu.lst-entry that has the /dev/sdb and replaced by /dev/sda
    Starting the system, I have to choose the system.

XOrg
After booting, I had some Problems starting the X-Server. This is clear. When you start the stick on system that has a different Graphics Adapter, your etc/X11/xorg.confwill not allow to start your X-Server.

So I just deleted the file /etc/X11/xorg.conf. The system itself creates a temporary (when not optimal) configuration.

So, It works now on different Hardware.
I have unistalled all the big packages like games and asian fonts.
To find the big packages, I used kdirstat.
I installed
[LIST]
[*]Gnome
[*]    OpenOffice
[*]    Java VM 1.6
[*]    eclipse
[/LIST]

---

