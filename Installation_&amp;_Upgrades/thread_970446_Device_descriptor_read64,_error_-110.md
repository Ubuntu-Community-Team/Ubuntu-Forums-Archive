---
title: "Device descriptor read/64, error -110"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by piwi on 2008-11-04
Today I decided to do a clean install of Kubuntu 8.10 because I had ****** up Ubuntu a bit. Installation went well, but afterwards when starting up the computer, it is very slow starting up and gives several errors.

USB 1-4: Device descriptor read/64, error -110
USB 1-4: Device descriptor read/64, error -110
USB 1-4: Device descriptor read/64, error -110
USB 1-4: Device descriptor read/64, error -110
USB 1-4: Device descriptor read/8, error -110
USB 1-4: Device descriptor read/8, error -110
USB 1-4: Device descriptor read/8, error -110
USB 1-4: Device descriptor read/8, error -110

All these errors take more than a minute and after these errors the computer starts up oke.

Previously with Ubuntu I had a bit of the same problems but I used an external USB hub to solve the issue, but in my opinion this is not the solution. And I kept having problems with my printer, which could not be recognized by the computer before I had unplugged and plugged int the USB cable in the external hub several times. 

I really want to resolve this issue, because I want to use my USB devices in a normal way. 

Thanks in advance.

---

### Post by pbournho on 2008-11-05
I have the same message on Ubuntu 8.10; when a logitech quickcam pro 9000 (046D:0990 ) is connected

---

### Post by piwi on 2008-11-05
Does nobody know what causes these errors and what I can do about them?

When I used Kubuntu 7.10 before I had no problems at all, can it be caused by a kernel update or something?

Anyone?

---

### Post by maxcelpc on 2008-11-06
Message deleted

---

### Post by maxcelpc on 2008-11-06
I have the same problem on only one of four computers running Ubuntu 8.04 Hardy and 8.10 Intrepid. The problem has existed since at least Hardy and seems to affect only certain motherboards. It is associated with the ehci_hcd USB2.0 controller in the kernel.

I haven't found a solution yet, but one way round it is to disable the onboard USB2.0 controller in the BIOS. Alternatively run the code

```
sudo modprobe -r ehci_hcd
```

which will remove the USB2.0 controller from the kernel.

The down side to both these fixes is that USB interfaces will be only USB 1.0/1.1, which will make transfers from large mass storage devices very slow indeed.

I have spent hours reading post and bug reports, but the development team do not seem to acknowledge this a a valid bug.

---

### Post by piwi on 2008-11-07
Thanks for your reply. Though disabling USB 2.0 doesn't seem to be a good solution for me or in general I think. 

Would it be an idea to file a bug report also, so it comes to the developers attention one more time?

For now I think I only will plug in my printer when I need it. My external harddrive has no problems.

---

### Post by becatlibra on 2008-11-07
I have this trouble with a WD250G MyBook.  At first I thought it might be a filesystem issue (I had formatted it to NTFS long ago) - I dropped all files and reformatted to ext3.  Everything SEEMED okay until, in the middle of an rsync, I received 


"rsync: writefd_unbuffered failed to write 4 bytes [sender]: Broken pipe (32)"

It unmounted itself.  Then, in the logs, back to the same error message:

"device descriptor read/8, error -110 " over and over

---

### Post by Allochtoon on 2008-11-23
All my usb storage devices have this issue only on this box. 

Not a valid bug? WTH?

---

