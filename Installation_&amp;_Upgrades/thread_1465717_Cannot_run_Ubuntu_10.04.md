---
title: "Cannot run Ubuntu 10.04"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by dennisjac on 2010-04-29
Hi,
I'm trying to check out the new Ubuntu release but run into trouble.
The first thing I tried is installing it into a KVM VM. This works but whenever I move the mouse on the Ubuntu desktop Xorg CPU usage goes to 99% basically making the desktop unusable.

The second thing I did was to write the ISO to a USB stick and boot the machine from that. This works and I get the grub menu but when i select to just live-boot the cd without installing it I just get a *beep* sound from the speaker and get back to the menu. This also happens when I just let the menu countdown to 0. A *beep* from the speaker and the countdown starts over again in a loop.

How can I test Ubuntu without killing my currently running system?

---

### Post by slvr42 on 2010-04-29
Have you tried installing it to a Virtual Box?

---

### Post by dennisjac on 2010-04-29
No and right now I've no plans to install VirtualBox. I have several instances of Fedora, Centos, Ubuntu server and Windows setup using KVM and they all work fine. I'd prefer the live-boot option anyway as that would actually let me determine if this release works all right on my hardware.

---

### Post by canerunner on 2010-04-29
Is the system configured to boot from the USB?

In my experience, there is more to booting and running Ubuntu from a USB than just burning the ISO to it. It's been a while but I think there was a procedure to make the thumbdrive bootable.

I know that you can run the USB startup disk creator from 9.04 or 9.10, but that makes a bootable USB key with that system on it. I can't remember what I had to do to install a bootable system of a different flavor on the key.

---

### Post by dennisjac on 2010-04-29
The USB stick boots fine since I get the Ubuntu boot menu rather than the usual Fedora boot menu. It's just that when I select the first option all I get is the beeping speaker and the menu resets.

---

### Post by dennisjac on 2010-04-29
BTW I used the LiveCD tools to create the stick:

livecd-iso-to-disk ubuntu-10.04-desktop-i386.iso /dev/sdc1

where /dev/sdc look like this:

```
Disk /dev/sdc: 4002 MB, 4002910208 bytes
124 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 7688 * 512 = 3936256 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1016     3905473   83  Linux
```

This works fine for the Fedora desktop ISOs.

---

