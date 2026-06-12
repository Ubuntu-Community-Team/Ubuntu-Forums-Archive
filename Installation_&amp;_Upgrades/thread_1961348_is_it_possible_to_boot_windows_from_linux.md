---
title: "is it possible to boot windows *from* linux?"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by hlb on 2012-04-19
hi everyone,

not talking about VMs, but "chain loading" an existing windows installation.

grub and the like unfortunately doesn't seem to be viable options since I'm dealing with a Bluetooth keyboard 
=>
i need a working bluetooth/HID stack *before* interacting with the system and triggering the windows load sequence.


what you'd suggest?


in alternative, is it possible to choose the boot option via a (... plain usb dongle RF thing, not BT) *mouse* instead of the keyboard?


thanks a lot in advance!

---

### Post by albandy on 2012-04-19
sudo grub-reboot 1

the number means this:
0 first grub entry
1 second grub entry
2 third grub entry 
...

---

### Post by codemaniac on 2012-04-19
> **hlb said:**
> 
in alternative, is it possible to choose the boot option via a (... plain usb dongle RF thing, not BT) *mouse* instead of the keyboard?


This point seem to be of interest . Theoretically to achieve that you need to be a herculian coder .Unlike keyboard mouse needs to be either polled pretty quickly or be used with interrupts.Should you need to define some mouse specific events like click() and all that are missing right as of now .Below is the grub developers mailing list .
[https://lists.gnu.org/mailman/listinfo/grub-devel](https://lists.gnu.org/mailman/listinfo/grub-devel)

---

### Post by Mark Phelps on 2012-04-19
It reads like what you want to do is enable device(s) in Linux and then boot into Windows, while still inside Linux.

The only way I know that can be done is with a Virtual Machine -- but that doesn't sound like what you want.

I don't believe you can do this using GRUB because all it does is hand over control to the Windows Boot Loader -- and when that boots, Linux is no longer running.

---

### Post by sudodus on 2012-04-19
> **albandy said:**
> sudo grub-reboot 1

the number means this:
0 first grub entry
1 second grub entry
2 third grub entry 
...
+1
I didn't know of grub-reboot, but I read ```
man grub-reboot
```
> Set the default boot entry for GRUB, for the next boot only.

and I think it will do what you want, *hlb* :KS

---

### Post by hlb on 2012-04-19
thanks for the replies, one seems exactly on mark and immediately usable and I'll employ it as soon as i get my hands back on the pc,

the other is interesting in a broad sense, 

and together they me wonder if anyone tried to write a bootmanager-of-sorts based not only the grub codebase but using an ***extremely*** reduced linux installation with the necessary drivers, bootable code and some libraries to e.g. poll the mouse .....


(to clarify: i'd like to swich OSes and not to let linux manage the devices, it's just another form of dual-booting with the necessity to interact with the system for a short while to select "boot on the OS installation 2" with the bluetooth stack running)

---

### Post by oldfred on 2012-04-19
Is the issue configureing the bluetooth mouse & keyboard?

Sharing bluetooth mouse between Windows and Ubuntu 
[http://ubuntuforums.org/showthread.php?t=1479056](http://ubuntuforums.org/showthread.php?t=1479056)
[http://ubuntuforums.org/showthread.php?t=764756](http://ubuntuforums.org/showthread.php?t=764756)

---

