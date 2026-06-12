---
title: "unexpected reboot after uncompressing kernel"
date: 2006-03-23
forum: Installation &amp; Upgrades
---

### Post by the mikey on 2006-03-23
Every time I load the installer, and select an option for installation, it loads vmlinuz, initrd, and then goes to a new screen where it says it's uncompressing something, and then booting the linux kernel.

At that point, my computer reboots, and after the initial boot jobs (detecting ide drives, etc.), it brings me back to the same installation screen. So, i hit enter again, and it does the same round of things.

I've tried booting with noacpi, as well as disabling the probing of usb drives, but it all results in the same failure.

I had a similar problem with fedora, a day before i tried installing kubuntu. It would load vmlinuz, then initrd, then it would say it's uncompressing something, booting the kernel, and then it would fill my screen with

```
unknown interrupt or fault at EIP 00000060 c0100231 00000230
```

and reboot.

Only difference with kubuntu is, it doesn't show those errors.

Here's a screenshot of fedora with the errors: [http://the.photos.cx/P1010002-1142989708.JPG](http://the.photos.cx/P1010002-1142989708.JPG)

I downloaded this file: kubuntu-5.10-install-i386.iso

checksum:

1dae9ca81cf3eb1dbe7966f39a39daf3 *kubuntu-5.10-install-i386.iso

I did try setting it to log boot errors, but it didn't show anything. Now that I think about it, that's probably for a system that's already been installed. 

It's been said that I should try an older version of the installer, something running the 2.4 kernel. I'm not too crazy about that idea. 

Computer is an HP Pavilion a712n. 

Please help.

---

### Post by the mikey on 2006-03-24
I managed to get it installed by adding acpi=off into the boot line. Now, I have a new problem. When booting with the splash, it will hang forever when loading the hotplug subsystem. When i turn off the splash, it will give me all this: 

[http://the.photos.cx/P1010012-1143175076.JPG](http://the.photos.cx/P1010012-1143175076.JPG)

---

