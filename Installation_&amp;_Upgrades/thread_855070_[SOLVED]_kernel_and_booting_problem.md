---
title: "[SOLVED] kernel and booting problem"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2008-07-10
I am using 7.10, and yesterday, on my usual machine, I created a live USB stick of ubuntu 8.04.1 (with persistence facilities), following instructions. It worked ok and I used it to run an eeepc 900 and even install a dual boot 8.04.1 into the eeepc   :-)  During the process, I had to unpack initrd, edit a script and repack, because there was known to be a simple error in a script. All good stuff, but I was following blindly, so there is a chance I gently screwed something up in my machine :-( maybe.

When rebooting my usual machine this morning - this may be the first time I rebooted since my usb adventures yesterday - I find that the machine hangs at  an early stage - it is showing the kubuntu logo (my default session) and a start of the progress bar, but the progress bar does not progress......

The grub default kernel choice is
Ubuntu 7.10, kernel 2.6.22-15-generic
and this is the choice which causes a hang.
The earlier one (-14 at the end) works ok, 

In menu.lst I have now commented out the references to
Ubuntu 7.10, kernel 2.6.22-15-generic
and in /boot/  I have renamed any -15 related file with a leading # in the name, presumably putting it out of action (?)

My guess was that I had somehow corrupted an intrd or even a kernel file (?)
My cunning plan is to remove  the non working -15 related stuff and  expect another kernel update to automatically replace it. Not really knowing what had gone wrong with the booting, this seemed a good plan.

However, when I now run Update manager, no kernel updates are offered, so I wonder how to prompt a kernel update?

Suggestions about the apparent booting problem, my temporary solution and my cunning plan (failed) would be most welcomed.

---

### Post by PmDematagoda on 2008-07-10
Try booting the -15 kernel in Recovery Mode and see if it boots properly. If it doesn't, post the errors here.

---

### Post by candtalan on 2008-07-10
Thanks for the response!

Loading please wait ...
warning: couldnt open directory /lib/modules/2.6.24-19-generic: no such file or directory
fatal:could not open /lib/modules/2.6.24-19-generic/modules.dep.temp for writing:no such file or directory
[30.299538] input: AT translated Set 2 keyboard as  /devices/platform/i8042/sior0/input/input1
begin loading essential drivers... 
done
begin running /scripts/init/premount ...
done
begin mounting root filesystem ...
begin running /scripts/local-top ...
done
begin waiting for root file system ...
done
check root= bootarg cat /proc/cmdline or missing modules, devices: cat /proc/modules ls /dev
alert!  /dev/disk/by-uuid/6d764b5a-722f-4868--a712-4f32182bc3eb does not exist. dropping to a shell!


comment - it then goes to to (initramfs) prompt
comment - the kernel it looks for seems to be the ubuntu 8.04 ( -19) which is what I was using yesterday for the usb activity, and not the ubuntu 7.10 stuff it needs now ( -15)
comment - I can use the ( -14) to run the system of course, an dedit stuff. Thi sis also a dual boot PC with 8.04 on a different partiton  also, so I have in theory plenty of hopefuly convenient ways to edit files.

Thanks

---

### Post by Malac on 2008-07-10
Boot into -14 kernel
Then run:
```
 
sudo update-initramfs -u
sudo update-grub

```
Then reboot and try -15 kernel.
 
Edit :
looks like you've edited /boot/grub/menu.lst to point to a kernel you don't have installed (2.6.24-19-generic) this is probably on the USB drive
 
> **candtalan said:**
> alert! /dev/disk/by-uuid/6d764b5a-722f-4868--a712-4f32182bc3eb 
is probably you're USB uuid

---

### Post by candtalan on 2008-07-10
Thanks for the response!
@Malac:
I did this but there was no improvement, and anyway the menu.lst looks ok. Strange. 
So I wondered if the item called the -15 kernel was somehow pointing to a -19 module (?). anyway I found a reinstall comment on a related subject which gave reinstall of linux image:

sudo apt-get update
sudo apt-get --reinstall install linux-image-2.6.22-15-generic linux-image-virtual

(comment - in hindsight the virtual probably is not relevant for me, but never mind.....)

It did not look like it would do any harm ;-) so I gave it a go, and it has worked. So it looks as if my linux image -15 was bad in some way.
Now, because I have just gratuitously added a linux-image-virtual, this has appeared in menu.lst and in /boot/ variously, but I have commented these out. It still works :-)

Many thanks for the respnses.

---

