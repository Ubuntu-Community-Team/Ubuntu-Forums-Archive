---
title: "Upgrading to dapper cannot boot."
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by eising on 2006-06-08
EDIT: See my last post for the fix
Hello.

I cannot install dapper, so I tried to install breezy and then upgrade. That was no problem at all, but when I tried to boot it, it stalled at mounting the root file system, and after a while, I got this one:
```

ALERT! /dev/hda4 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off

```

I tried to boot it in the recovery mode, and sure enough, when it checks my harddisks, it only finds /dev/hda1.

The last line before it stops is the loading of hid_core.

I've tried to disable usb2 and to disable usb legacy support with no effect.

I have a p4 3ghz on an Asus p4p800-x, with 2 80gb harddisks. One is /dev/hda, the other is at another ide controller, as /dev/hde.

Breezy btw runs perfect, but I really need some of the updates in dapper.

---

### Post by Ivan Matveich on 2006-06-08
Maybe dapper now sees your disk as /dev/hd[something else]?

You might try appending

```

root=/dev/hdb4 init=/bin/bash rw

```

to your kernel command line in grub. Also try "hdc", "hdd", "hde", whatever...

---

### Post by eising on 2006-06-08
Thank you for your reply, but I am not at all sure that it would help. You see, the breezy kernel works fine. Moreover, if I scroll through the kernel output I see it finds the relevant harddisks such as hda, hdc and hde. No other devices are added there that might have been a mis-translations of the first harddisk.

---

### Post by mlwmohawk on 2006-06-08
[QUOTE=eising]Hello.

I cannot install dapper, so I tried to install breezy and then upgrade. That was no problem at all, but when I tried to boot it, it stalled at mounting the root file system, and after a while, I got this one:
```

ALERT! /dev/hda4 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off

```

I tried to boot it in the recovery mode, and sure enough, when it checks my harddisks, it only finds /dev/hda1.

The last line before it stops is the loading of hid_core.

I've tried to disable usb2 and to disable usb legacy support with no effect.

I have a p4 3ghz on an Asus p4p800-x, with 2 80gb harddisks. One is /dev/hda, the other is at another ide controller, as /dev/hde.

Breezy btw runs perfect, but I really need some of the updates in dapper.[/QUOTE]

This looks like my problem "RANT: Waiting for root," the problem is that the Ubuntu crew knew about this bug but the fact that it renders you unable to boot didn't seem to bother them.

The IDE drives on your PCI IDE controller are being enumerated first, so hde is probably your hda and vice versa.

Test: Comment out the "hde" drive in fstab, remove PCI IDE controller and see if you can boot. If you can, welcome to the club.

There is no fix, just work arounds.

---

### Post by eising on 2006-06-08
Ok, I'll just wait for an update to this problem before I upgrade again... Meanwhile I have the dapper source in my sources.list, so I am apt-get source'ing the packages I need...

---

### Post by eising on 2006-06-09
I was wondering, if it was possible to get around this problem by compiling a custom kernel? I suspect that the ide controler is loaded directly into the kernel or if as a module, loaded before the rest of the ide modules. I will test if this can be solved with a custom kernel.

---

### Post by metoo on 2006-06-09
You may have to wait a long time for the update. Not sure that it really is a bug.
The new kernel simply identifies the IDE chip sets in reversed order.
So /dev/hdaX became /dev/hdeX (assuming the different IDE chip set has as well 4 ports)
That's why Ivan recommended trying the different device ids before.

You can do this by changing from within grub hit e and not enter when selecting the new kernel version. b to boot.
Or you can change the entry for drapper in /boot/grub/menu.lst while running breezy.

---

### Post by PesVseved on 2006-06-09
Well.........

I got this problem only when my laptop's docked......

When I change hda to hde in grub. It boots........, but has no swap parition........Actually it has one, but is not using it because it hda4 not hde4

I don't know what to do.........

---

### Post by eising on 2006-06-09
I might have a solution, allthough I havent tested it yet. Try appending the option ide=reverse to the kernel. It might work. I'm gonna test it in a second.

---

### Post by metoo on 2006-06-09
PesVseved,

you may need to edit the device line for your swap partition in /etc/fstab .
E. g.:
sudo gedit /etc/fstab

---

### Post by PesVseved on 2006-06-10
I edited my fstab. It looks like this

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,unhide,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

/dev/hde5       none            swap    sw              0       0 

```

I also changed my grub, so that I could boot even if my laptop's docked:

```
title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/[COLOR="Red"]hda1[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (docked)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/[COLOR="#ff0000"]hde1[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot
```

I know this not a real solution, but it works.......
This bug is an important one and I think it prevents some people from using dapper.........

---

### Post by eising on 2006-06-10
I have the solution now. The solution is to use e2label instead of direct names. So boot up on a live cd, and run e2label /dev/hdxy label. For example use e2label /dev/hda1 root.

Now you can change /etc/fstab and replace /dev/hda1 with LABEL=root

To change the swap partition, run mkswap /dev/hda2 -L swap (if hda2 is your swap partition)

Remember to change /boot/grub/menu.lst, updating root=/dev/hda1 to root=LABEL=root if your label is called root. This effectively solves the problems.

---

### Post by NickeM on 2006-06-12
Hi, i think i have the same problem:
ALERT! /dev/hdb1 does not exist. Dropping to a shell!
/bin/sh: can't access tty; job control turned off

This happens when i boot on the 2.6.15-23-686, if i boot on the 386 kernel it works?!

My filesystem is reiser4 so my question is how do i change the label on the device  since i cannot use e2label(only for ext2/ext3).

---

