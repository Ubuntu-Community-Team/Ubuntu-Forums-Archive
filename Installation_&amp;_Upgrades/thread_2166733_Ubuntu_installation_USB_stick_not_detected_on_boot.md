---
title: "Ubuntu installation USB stick not detected on boot"
date: 2013-08-10
forum: Installation &amp; Upgrades
---

### Post by bearl2 on 2013-08-10
Hello all,

I'm trying to make a USB stick from which I can run a live Ubuntu 12.04 desktop without installing.  I believe the process for this is the same as any normal installation, only I click 'try ubuntu' instead of 'install.'  I am currently running Ubuntu 12.10. To do this, I followed the following instructions: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu)

My problem now is that, upon startup, the USB stick isn't recognized and I thus cannot boot from it.  I've tried on both a Thinkpad t60 and a Thinkpad e420 with the same results.  I have used this same usb stick to install ubuntu before (I've wiped it since), and the usb stick works perfectly otherwise, so I don't think it's a problem with that.  I have tried going to the BIOS and changing the boot order, but to no avail.

Does anyone see what I'm doing wrong?  Thanks so much!

Edit: Whoops, it turned I had changed the formatting on my usb stick a while back.  I reformatted it to fat32 and everything works fine.  Silly mistake; sorry for wasting your time.

---

### Post by SweetAurora on 2013-08-10
The startup disk creator has been creating havoc lately. Instead use DD. It's a program that clones drives and writes iso's.
First open the Gnome Disk Utility, might be just "Disks" and see where the usb is mounted, like "/dev/sdX"
Then open the terminal and type:
```
sudo dd if=/path/to/iso/file.iso of=/dev/sdX
```
Wait till it finishes before closing the terminal.

DD is more reliable than the program that comes with Ubuntu. Be aware, if used wrong, it can wreak havoc on your system. DD is sometimes called "Disk Destroyer" because it will happily write the ISO over your main drives if you set the paths wrong.

---

### Post by VMC on 2013-08-10
You may be suffering from the bug report I filed. What's the kernel number *uname -r*.

Open up a terminal and monitor syslog:
```
tail -f /var/log/syslog
```

After you start monitoring then plug in the USB device and watch. Wait 5 minutes, it may get mounted.

---

### Post by ubfan1 on 2013-08-10
Are you at a black screen with a flashing cursor?  Do any error messages eventually appear (after a few minutes)?  Saw an installation complaint about missing media /dev/sdb ... which should have been the usb stick.  Took drastic action of yanking stick, and replacing, which fixed the issue and allowed installation to continue normally.  Thought problem was just flakey USB on the laptop getting the install.

---

