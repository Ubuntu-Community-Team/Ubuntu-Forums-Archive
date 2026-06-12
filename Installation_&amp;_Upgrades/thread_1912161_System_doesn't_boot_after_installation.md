---
title: "System doesn't boot after installation"
date: 2012-01-20
forum: Installation &amp; Upgrades
---

### Post by Rabenschwinge on 2012-01-20
I've tried to install Ubuntu 11.10 from a 64-bit Desktop CD onto an external harddrive, /dev/sdb during installation. When I was asked where I want the bootloader installed I chose /dev/sdb's master boot record. I don't want Ubuntu to touch the internal hard drive, not at all.

When I choose that drive in BIOS as startup device the only thing I see is a blinking cursor. No message from GRUB, not even an error message.

It *might* be so that the order of the drives changed, and that the drive that is booted from is always the first device... but I am not sure and even if so I wouldn't know how to fix that in the GRUB installer.

In posts in different forums I was asked to let an analyzis script for GRUB run, the result are posted here:
[http://pastebin.com/ubc5xqgi](http://pastebin.com/ubc5xqgi)

Does anyone have a suggestion where to go from here?

---

### Post by carl4926 on 2012-01-20
What you should do is install with the external as first boot device and leave it this way.
Probably quicker for you to do that

---

### Post by darkod on 2012-01-20
It looks fine. Have you tried running the cd in live mode to see if it works fine?

The black screen might be a video issue. Usually the same would happen if you try to boot live mode, if the problem is the video.

---

### Post by Rabenschwinge on 2012-01-20
@carl
I cannot change the order of individual drives in the BIOS, I can only change the order in which it looks for a possibility to boot.

Even when I put USB Sticks & Drives in front of the internal drive in the boot sequence, and then force it to actually start from a CD, the internal drive is /dev/sda and the external one /dev/sdb... It just might be that that is not so if I actually start from /dev/sdb.

The only way I see to force this is to remove the internal drive... in which case I would loose the warrenty for the computer.

@darkod
The screen isn't just black, there is a blinking cursor. Absolutely nothing happens. No message that GRUB starts, no message that the kernel is being loaded, no drive activity.

I can start from the live cd and even chroot into the system if I like, but I cannot start the system itself.

You must take into account that the error condition, if it is as I suspect, only occurs when you're actually trying to boot from the target device, /dev/sdb during installation. The dump was created after booting from a life CD, thus, it is expected to look fine, yet the error exists.

---

### Post by carl4926 on 2012-01-20
You could just use a Utility CD to boot with
Like SuperGrubDisk

---

