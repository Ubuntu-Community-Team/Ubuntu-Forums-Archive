---
title: "Computer won't boot after shutting down with windows 7 and Ubuntu dual boot"
date: 2014-12-29
forum: Installation &amp; Upgrades
---

### Post by CobyCobie on 2014-12-29
I got my computer to successfully dual boot Win7 and Ubuntu this morning.  Sometimes (maybe half of the time), when I shut the computer down and try to start back up, I get an error.  It gives me a blinking underscore for a few minutes and then says something along the lines of "no media device found, please enter a valid device then reboot"  That isn't at all what it says, but it's close enough.  Basically, I think it doesn't recognize my hard drive, even though it is shown as the first boot option in the BIOS.  I can temporarily fix the problem by running boot repair on the Try Ubuntu option from a usb drive, then I have to do the update-grub thingy in the terminal to get it ti detect Windows.  It works all fine until I decide I need to shut down the computer, and then I get the problem described above.  I have probably done this 10 times in the past 2 days, and would not like to have to do it every time I want to reboot or shut down.  I am thinking it is a Linux-related issue because it usually boots into the GRUB menu if it reboots correctly.  I have attempted to do research, but I so far I been unsuccessful.  Help?

---

### Post by oldfred on 2014-12-29
When you get error message, wait 10 or 20 seconds and press enter. See if that works.
Sometimes it seems drives spin down and do not come back up quick enough.

Some have changed from UUID to device in grub, but that is not recommended.
I think the search line in grub menu has to search all devices BIOS reports on every boot and if not ready then that is the issue.

---

### Post by CobyCobie on 2014-12-29
Thank you for the quick reply, I will wait a minute and try that as soon as I can get it to happen..  If it does not work, I will be back as soon as I can get my system back up and running.

EDIT: Problem has not shown itself since this thread was started, which was probably 10 reboots.

---

### Post by CobyCobie on 2014-12-31
Sorry to double post, but...

The problem continues!  I reinstalled Ubuntu, defragmented my Windows drive, and will see if I can do it on Ubuntu (I'm sure I can, I am confident I can figure it out).   I realized I can just do a disk repair from my USB drive with the Ubuntu installer, and that fixes the problem temporarily.  The solution mentioned two posts above did not work, even after waiting minutes, so I need to know any other possible solutions?

EDIT:  Just read about defrags, I wont do that then...

---

### Post by efflandt on 2015-01-02
Not sure if this is a factor or not, but when grub2 first came out some time ago, the part of it in the mbr was larger than the part of the mbr in use by DOS/Win. Some Windows programs stored some data in what they "thought" was an unused part of the mbr, which tended to step on grub2 and make it not work. I ran into that with DellDatasafe program. At that time if I had grub in the mbr of my primary drive, once I booted Win7, I could no longer boot. So I have a second little Ubuntu system on my second drive (SSD) and have my BIOS set to boot grub in the mbr of that drive. That extra little Ubuntu system also came in handy while recently installing Ubuntu 14.04.1 on my main drive, to be able to check the logs and realize that nouveau and the ancient nvidia-current drivers did not support my new video card with Maxwell chip (got it working now with newer nvidia drivers). 

The developers of grub have tried to not use parts of the mbr that those Windows programs are known to use, but you might have some Windows program storing something in the mbr that they are not aware of.

---

