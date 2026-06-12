---
title: "Boot to Flash drive fine, but then no file systems found"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by rob106 on 2014-10-27
[COLOR=#333333]I have a brand new ASUS x551ma laptop. I'm trying to ditch Windows and do a full Ubuntu 14.04 install. I updated and changed the BIOS to allow USB booting and created a bootable 8GB stick using pendrive.

Now I can startup from the USB stick, but it just gets to the GRUB 2.02 prompt. ls will list several drives and partitions, but if I try to find or list files on any of them, I get "unknown filesystem". Except (memdisk) which just has grub.cfg.  I can't use any other methods I've found for booting from GRUB or changing configuration because nothing is accessible.

If I exit or boot without the stick, the machine will still boot to windows and I have access to all the files on the stick. Every suggestion I've found is already on there. Is there a BIOS setting or particular file I should be looking for which will allow any of my drives to be available in the boot loader?[/COLOR]

---

### Post by nerdtron on 2014-10-27
Much like a problem like installing windows 7.
I saw this [http://www.tomshardware.com/answers/id-2056433/replace-win-win-asus-x551ma-laptop.html](http://www.tomshardware.com/answers/id-2056433/replace-win-win-asus-x551ma-laptop.html)

MarcT said
"I Bought the same one. You do have to have the latest bios. I believe  5.0.2. Get it from their support site. Once that is updated you have to  go into bios by holding f2 after reboot. Go to Advanced and turn off  secure boot. Then under Boot There will be an extra command regarding  launch or enable CSM. You have to disable the command above that one to  enable the Launch CSM. Modify those save and exit reboot and press ESC  to get to boot selection.  Doing this from memory but should be 90%  accurate. Hope this helps."

Better have all BIOS setting to support legacy.

I ran into a similar problem before with a win8 lenovo laptop. I ended up erasing everything, updating BIOS, changing UEFI and deleting all hard drive partitions. Then successful boot from USB.

Other experts here may suggest other things.

---

### Post by sudodus on 2014-10-27
Hi Rob,

Welcome to the Ubuntu Forums :-)

A new computer with Windows: I suspect that you have UEFI (not the old style BIOS), and it makes it harder to install Ubuntu, but still possible. *Edit*: This issue is already addressed by *nerdtron*.

-o-

Maybe you mean Pendrivelinux, when you write that you used 'pendrive' to create the bootable 8GB stick. In that case I suggest that you use another tool. If you create it in linux, try mkusb, if you create it in Windows, try Win32 Disk Imager. These tools are particularly suitable right now if you want to install the new version of Ubuntu, 14.10. (There are several good tools for 14.04.1 LTS, which soon will work also for 14.10.)

See the description in the following links

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb) and  [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

There is a more general wiki text at [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

Finally, [try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by rob106 on 2014-10-27
Yes, I meant Pendrivelinux. I'm only using 14.04 because that's how long I've been working on this. I'll give Win32 Disk Imager and 14.10 a try. It is UEFI system. I'm old and the setup screen is identical to older BIOS systems. So I'm stuck calling it that. I'll learn.

As for the BIOS changes recommended in the first reply, I did all that. I am now using ver 512. It came with ver 510 anyway. So the update probably wasn't necessary. The computer has no problem seeing and trying the USB first for boot. It just can't see enough of the drive.

Thanks for the help so far.

---

### Post by sudodus on 2014-10-27
***Please stay with 14.04.[COLOR=#ff0000]1[/COLOR] LTS*** !!!

It is more polished and debugged, and more likely to work well. Furthermore lt will last longer, until April 2019, while 14.10 only lasts 9 months.

I'm not sure Pendrivelinux works well with UEFI. The tool ***Unetbootin*** works well (I would recommend that as well as ***Win32 Disk Imager***) for the Ubuntu 14.04.1 64-bit desktop iso file.

```
 ubuntu-14.04.1-desktop-amd64.iso
```

---

