---
title: "GNU GRUB version 1.99-21ubuntu3.1 ERROR"
date: 2012-09-20
forum: Installation &amp; Upgrades
---

### Post by ElbaneDark on 2012-09-20
Hey guys I just installed Ubuntu 12.04.1 on an HP mini 110 previously running windows xp.

I had been having trouble with this laptop for a long time and I couldn't find any help with doing a factory reset. So, I decided to put linux in order to erase the windows partition and have linux as the default OS. Well, everything went well as far as installing but after it was done installing the laptop reset and I kept getting the GNU Grub...

I had to reset every time with the UBS and change the boot priority so it could go into linux. Once I was back in the linux OS I was reading a forums with suggestions on how to get rid of the GNU Grub screen and load Linux normally without having to have the USB inserted. 

I went into the shell and mounted sudo /dev/sdb2  etc and once I restarted the computer the GNU Grub was still there, however this time even if I changed the boot option to the USB it still goes back to that damn GNU GRUB...

Can anyone please help me with this problem, I'm basically stuck on the GNU GRUB screen and would like to fix it, thanks.

---

### Post by darkod on 2012-09-20
Hold on, try to explain more precisely.

Are you trying to say that it boots correctly with the usb but not without it?

In that case, grub2 probably installed on the usb stick since you booted from there to start the install.

Boot once with the usb connected, and open terminal. To see the disks and partitions listed, execute:
sudo fdisk -l (small L)

In most cases, the hdd will be /dev/sda and the stick /dev/sdb.

If that is true, to install grub2 onto the MBR of the hdd, execute:
sudo grub-install /dev/sda

If in your case the hdd is /dev/sdb, just use that in the command instead of /dev/sda.

Reboot without the stick and it should work.

---

### Post by ElbaneDark on 2012-09-20
> **darkod said:**
> Hold on, try to explain more precisely.

Are you trying to say that it boots correctly with the usb but not without it?

In that case, grub2 probably installed on the usb stick since you booted from there to start the install.

Boot once with the usb connected, and open terminal. To see the disks and partitions listed, execute:
sudo fdisk -l (small L)

In most cases, the hdd will be /dev/sda and the stick /dev/sdb.

If that is true, to install grub2 onto the MBR of the hdd, execute:
sudo grub-install /dev/sda

If in your case the hdd is /dev/sdb, just use that in the command instead of /dev/sda.

Reboot without the stick and it should work.

Yes, well I was able to boot correctly from the USB stick until I  installed Grub from the prompt. I installed it on the /dev/sbd which is the USB stick and now I can't boot back into Ubuntu with or without the stick; it just keeps looking at that error message.

---

### Post by darkod on 2012-09-20
Well, how the hell did you miss the part where I said to install it onto the hdd????

Are you trying to boot with or without the usb? How did it make sense to you to install grub2 to the usb when you are trying to boot without it?

Anyway, lets get down to business. No need to try to boot with the usb right now, since you overwrote the bootloader on it. Although you should still be able to boot with the stick connected, but lets forget that.

When you try to boot the computer without the stick, there is a grub2 message/error and you receive something like a grub rescue> prompt, right?

In thet prompt, type:
ls (small LS)

hit Enter, and tell us what is the output.

---

### Post by ElbaneDark on 2012-09-20
Ok booting without the USB I get grub> prompt.

Typing ls (lowercase) I get (hd0) (hd0,msdos5) (hd0,msdos1)

*I messed this up before posting to the forum. I had been trying other things to no avail until I typed the wrong thing and bam.

---

### Post by darkod on 2012-09-20
OK, at that prompt execute these commands one by one, they should boot you successfully.

```
insmod part_msdos
insmod ext2
set root=(hd0,msdos1)
linux vmlinuz root=/dev/sda1
initrd initrd.img
boot
```

If that boots you, open terminal and do the:
sudo grub-install /dev/sda

and you should be good to go.

---

### Post by ElbaneDark on 2012-09-20
Ok I went one by one and when I got to "linux vmlinuz root=/dev/sda1 I get an error: invalid file name.

---

### Post by ElbaneDark on 2012-09-20
Ok don't know what I did but i'm back in with the USB inserted.

it is barely loading, I'll let you know if I can boot afterwards without the USB present.

---

### Post by ElbaneDark on 2012-09-20
Hey thanks for helping me out, I finally got it to work 100%!

---

