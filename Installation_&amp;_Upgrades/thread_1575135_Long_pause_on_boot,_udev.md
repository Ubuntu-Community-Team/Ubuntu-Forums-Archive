---
title: "Long pause on boot, udev"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by billstei on 2010-09-15
I am getting a long pause on boot-up of Ubuntu 10.04.1, and the last dmesg entry before the pause is this:

[    4.582912] udev: starting version 151

Pressing the escape key gets the boot going again, but intermittently I end up with no mouse pointer control (the pointer is visible).

Also, right before the grub menu appears I get:

error: file not found

---

### Post by billstei on 2010-09-15
After turning off ACPI features in the BIOS, there is no pause/hang anymore, but I am still not getting the mouse recognized reliably, although it seems to help to move the mouse while booting to get it recognized.

---

### Post by billstei on 2010-09-16
Apparently turning off ACPI features was not actually the reason for the pause (race condition?), but now I have "USB Legacy Support" disabled, and this seems to be the key.  The mouse is connected to a (single) PS2 port on the motherboard, and the BIOS sees this as a USB mouse.  If I don't move the mouse it ends up being non-active when I get to the Ubuntu login screen, so the question is whether anything can be done to get it working reliably without having to constantly move it during boot-up.  I should try an actual USB mouse to see if that is recognized consistently...

Update: Tried a USB mouse and am getting hang during bootup, but mouse seems to be recognized now.

---

### Post by billstei on 2010-09-17
I did the following to get rid of the "error: file not found" message:

1) Run grub-mkdevicemap.
2) Reinstall grub-common and grub-pc packages using Synaptic.

Probably 1) is not necessary as I think grub-pc runs it as part of the package installation procedure.

---

### Post by billstei on 2010-09-18
My best guess at this point is that the pause/hang is fsck/mountall/plymouth, and is a bug being tracked here: [https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563916](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/563916)  and is supposedly fixed with package plymouth - 0.8.2-2ubuntu4 which is not present in Lucid (yet) but is in Maverick.

---

### Post by Gerald here on 2010-11-15
Dear Billstei, 

   I got a similar or the same problem in 10.10. On boot-up my system usually hangs on a black screen, not even ctrl-alt-del works anymore; The only way I have yet figured out to prevent this seems moving my usb mouse during boot or unplug it and plug it in again after boot. I'll look at the site you posted and get back to you.

Regards, Gerald

Update: 0.8.2-2ubuntu4 presumably doesn't fix my problem, as I already got 0.8.2-2ubuntu5 installed
Update 2: In my case I think it was something with the splash screen, not the mouse (sorry). Apparently fixed it by following this thread [http://ubuntuforums.org/showthread.php?t=1491275&highlight=boot+splash+quiet](http://ubuntuforums.org/showthread.php?t=1491275&highlight=boot+splash+quiet)
Update 3: No, unfortunately it wasn't fixed by the thing above. I'm not sure what it is, maybe not the mouse, as unplugging it doesn't help; I just thought moving the mouse, or even more the touchpad, has a negative effect on crash probability. But that was just speculation and hasn't proven true. This is my problem actually: [http://ubuntuforums.org/showthread.php?t=1518789&highlight=recovery+required+filesystem+startup](http://ubuntuforums.org/showthread.php?t=1518789&highlight=recovery+required+filesystem+startup) .
Update 4: Changing the splash screen as described in this thread definitively fixed my problem: [http://ubuntuforums.org/showthread.php?t=1503509&page=2](http://ubuntuforums.org/showthread.php?t=1503509&page=2)

---

### Post by billstei on 2010-12-20
Changing the splash screen to solar did not help.  I think it might have something to do with doing fsck on my ReiserFS partition(s), which then hangs(?).

Edit: I am also watching this bug/thread: [https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647404](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/647404)

---

### Post by Syed75 on 2010-12-20
I get a 3 minute pause then it starts up. Don't know why.

---

### Post by billstei on 2011-01-19
I ran GPartEd Live CD 0.7.1 and did a reiserfsck on all the reiserfs partitions and there were no errors, so I don't think reiserfsck is waiting for user input.

Here is another potentially relevant bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/625395)

---

