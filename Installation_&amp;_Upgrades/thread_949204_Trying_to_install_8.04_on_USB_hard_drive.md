---
title: "Trying to install 8.04 on USB hard drive"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by viper1965 on 2008-10-15
I'm pretty new to linux, and would like to install 8.04 on my external Western Digital 500 Gb hard drive. I would like to be able to plug in the hd, boot, and be in Ubuntu. When I want Vista, unplug the usb, reboot, and be in Vista.

I blindly installed Ubuntu, putting it on the usb hd, the boot manager (forget what it's called) on the internal drive, and booted to Ubuntu with no problem. When I booted to Vista, it was trashed. 

I read an old post on here that said **never** put the boot manager on the internal hd, so tonight I put it on the usb, booted, and ubuntu said something like can't boot to the partition. I tried using the whole hd as a single partition, and making two separate ones. The computer is a Sony Vaio laptop with 2 Gb RAM. Its BIOS does support booting from an usb hd.

Please help,

Thanks,

Viper1965

---

### Post by rashhashan on 2008-10-16
hey man im trying to do the same thing except with a 4 or an 8 Gb thumb...please tell me when you find out

btw i hope this helps you out

[http://www.pcmech.com/article/ubuntu-804-persistent-install-to-usb-stick/]("http://www.pcmech.com/article/ubuntu-804-persistent-install-to-usb-stick/")

</break>

---

### Post by caljohnsmith on 2008-10-16
Viper1965, while you have your USB drive connected, boot your Live CD, open a terminal (applications > accessories > terminal) and please post:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] count=1 2>/dev/null | strings | grep -ie grub -ie "missing operating system"
```
So replace "sda" above with each of your drives. And finally, for each command above that returns "GRUB", please post:
```
sudo dd if=/dev/[COLOR="Red"]sda[/COLOR] bs=1 skip=1049 count=2 2>/dev/null | hexdump
```
And replace sda with the drives that previously returned "GRUB". That will greatly clarify what your present setup is as far as booting goes. :)

---

### Post by C.S.Cameron on 2008-10-16
I have had the same problem installing 8.10 from Live USB to a second USB device, (Flash drive).
My problem was that installer saw the Live USB as the first disk and in menu.lst on the destination drive wrote 'root (hd1,0)' when it should have written 'root (hd0,0)'.
If hitting 'Esc' at grub will give you a menu, you can edit this option by pressing 'e', you can test the option by hitting 'b'.
This will not make any permanent changes, but you can edit menu.lst after you are in.

There are linux tools for fixing the MBR in XP but not sure about Vista.

---

### Post by viper1965 on 2008-10-18
Thanks, caljohnsmith, but the first time I booted to the CD, I had no menu at the top of the screen, so I couldn't get to terminal. After that, I could not boot from the CD at all.

Changing hd1 to hd0 worked, C.S. Cameron!!!!!!!! How do you change menu.lst? I opened it, but don't have permissions to save it.Thanks!


Viper1965

---

