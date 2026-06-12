---
title: "Combine Drives : Ununtu and XP"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by technikalKP on 2007-08-13
Hi.

I recently installed Ubuntu on an older laptop.  I removed the existing Windows XP based hard drive prior to the install and put Ubuntu on a fresh hard drive all by itself.  Everything works just as I'd like, but there are some applications and data on the old windows drive that I still need to run.

Ideally, I'd like to combine both hard drives onto a single drive and either dual boot or have a Virtual Machine instance of the Windows drive available in Ubuntu.  If that's not feasible, I'd like to be able to boot or VM into the Windows drive when it's mounted as an external USB drive.  I just don't want to have to reinstall Windows.

Questions:
- Is this possible?
- If so, what approach would you recommend and why?
- Where are some good resources/how to guides on the recommended approach?
- if I boot to Windows as an external drive, will it screw up Ubuntu? Will the drive mappings screw up my windows apps?

Thanks for your help!

---

### Post by logos34 on 2007-08-13
VMware is a possiblity, but if you don't want to reinstall windows, AND this laptop can boot from USB device (check the bios--some older ones can't), then I'd put it in a USB caddy and boot from it that way.  Shouldn't mess anything up--you just change the boot order of the drives in the bios at startup.  You can propbably even avoid having to do that by adding a windows entry to /boot/grub/menu.lst allowing you to boot to the grub menu screen on the internal and select windows there--might look like this:
> 
title		Windows XP
root		(hd1,0)
map            (hd1) (hd0)
map            (hd0) (hd1)
makeactive
chainloader	+1

add a line for the external usb drive to /boot/grub/device.map.  So it might look like this:

(hd0) /dev/hda
**(hd1) /dev/sda**

0r 

(hd0) /dev/sda
**(hd1) /dev/sdb**

Get **fs-driver** for windows (adds support for  read + write to ext2/3 filesystem), and **ntfs-3g** for linux side (adds write support to NTFS)

You may be able to run some of your windows apps in linux using **Wine**.

---

