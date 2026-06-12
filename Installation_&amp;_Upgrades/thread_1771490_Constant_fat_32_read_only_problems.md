---
title: "Constant fat 32 read only problems"
date: 2011-05-30
forum: Installation &amp; Upgrades
---

### Post by Rgibbons on 2011-05-30
I am trying to use fat32 formatted external usb drives. I have tried every trick I can find here, but every time I mount my drives, they will only mount in read only. If I try to do anything with them I get a root only error.

I have tried reformatting them in Linux, tried using storage device manager. I will finally get it to where I can write on it only to find that the next time I try to used it I am back to square one again.

Can anyone help?

---

### Post by coffeecat on 2011-05-30
> **Rgibbons said:**
> If I try to do anything with them I get a root only error.

That sounds familiar. Did you, by chance install the package usbmount? If you did, uninstall it. That is what may be causing the problem. And if you have installed any other packages to "help" with usb-mounting, uninstall them as well. USB-autmounting works just fine out of the box in Ubuntu. Unfortunately there are some apps in the repositories not designed to be used with a GUI (usbmount is one) which are superfluous but which people install anyway and which cause problems.

What is "storage device manager"?

---

### Post by Rgibbons on 2011-05-31
storage device manager is listed as pysdm in the applications list. It allows you to set settings for drives in the fstab, but it has been no help either.

I did have usbmount installed, but uninstalling it did not help.

---

### Post by coffeecat on 2011-05-31
> **Rgibbons said:**
> storage device manager is listed as pysdm in the applications list. It allows you to set settings for drives in the fstab, but it has been no help either.

If it has written to your /etc/fstab, it might have been a positive hindrance. There could very well be an entry in fstab which is interfering. Post the terminal output of:

```
cat /etc/fstab
```Also, I notice that the package description for pysdm says:

> PySDM is a PyGTK-based Storage Device Manager that allows full customization
of hard disk mount points without the need to edit fstab manually.
It also allows the creation of udev rules for dynamic configuration of
storage devices.If it has changed your udev rules, it could really have messed up automouting of USB devices. Have you installed any other apps to "help" with USB mounting? We need to be clear: USB automounting works out of the box in Ubuntu. You do not need to install any extras packages. In fact there are several packages, usbmount being one, that cause more problems than they (allegedly) solve.

---

### Post by Rgibbons on 2011-05-31
I took out the line that storage device manager created. All that remains now is: 
UUID=9a4c8596-138f-4e4b-a795-ed1fc224f859  swap             swap  sw                                        0  0

the line I took out was:
/dev/sdb1 /media/data2 vfat defaults,user, noauto, dmask=027,fmask=137 0 0

---

### Post by coffeecat on 2011-05-31
> **Rgibbons said:**
> I took out the line that storage device manager created. All that remains now is: 
UUID=9a4c8596-138f-4e4b-a795-ed1fc224f859  swap             swap  sw                                        0  0

I hope that's not all that remains now. You need a root partition line at least, otherwise you will have an unbootable system.

> **Rgibbons said:**
>  the line I took out was:
/dev/sdb1 /media/data2 vfat defaults,user, noauto, dmask=027,fmask=137 0 0

The dmask and fmask values look OK, but there are spaces in the options field making it syntactically incorrect. The first is after "user," If the spaces were there in fstab, that might have been the problem.

---

### Post by Rgibbons on 2011-05-31
should I be using the UUID instead of the drive label if the label changes?

---

### Post by coffeecat on 2011-05-31
You can use /dev/sda1 type descriptors, UUIDs or partition labels in the first field. Clearly whichever you use has to remain the same. Did you mean a partition label for a fstab line?

---

### Post by Rgibbons on 2011-05-31
I was talking about whatever identifies the external usb drive.

---

### Post by coffeecat on 2011-05-31
Why bother with a fstab line for external USB drives? So long as a third-party application hasn't broken automounting for you, simply plug the drive in and it automounts.

---

### Post by Rgibbons on 2011-05-31
yes, it automounts okay, but in read only.

---

### Post by coffeecat on 2011-05-31
> **Rgibbons said:**
> yes, it automounts okay, but in read only.

Then you must have installed yet another package to "help" with usb mounting. There are several in the Universe repository that cause similar problems to usbmount. All are unnecessary. See if you can find anything that you installed which seems to fit this description and uninstall it. I'll see if I can find a recent thread that listed more of the problem packages than usbmount.

---

