---
title: "Error mounting /proc/bus/usb"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by HDTimeshifter on 2010-05-15
After upgrading to Ubuntu 10.04 LTS, I get the following error whenever I reboot:

> An error occurred while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery.

Pressing M doesn't work and after pressing S, I get the same error with /proc/bus/usb replaced by 0.  If I press S again, I am able to boot.  Anybody know what's going on here?

---

### Post by Prosa7 on 2010-05-15
I had the same problem but I managed to solve it. This is what I did:

1. open a terminal window from the menu: Applications > Accessories > Terminal

2. enter "sudo nano /etc/fstab" and enter your password when prompted.

3. add # in front of the line "none /proc/bus/usb usbfs devgid=123,devmode=644 0 0"

4. press <Ctrl> + <X> to exit

5. press <Y> to confirm saving the changes

6. Leave the file name to write "fstab" and press <Enter>

---

### Post by Prosa7 on 2010-05-15
.

---

### Post by HDTimeshifter on 2010-05-15
Does commenting out the line to mount the USB deactivate your USB ports?

The only USB device I use is my SD memory card connector - I'll hook it up after the next time I reboot, but if you can test one of your USB ports in the meantime to see if you have any problems, I'd appreciate it.

Thanks for the help.

---

### Post by Prosa7 on 2010-05-16
All my USB ports are working fine. In fact this is just a minor error. Apparently this was added in Karmic to force USB support in VirtualBox but it is no longer needed.

---

### Post by xisxas on 2010-05-16
Hi,

I get in the terminal:   usbfs                   /proc/bus/usb           usbfs   devgid=14 0 0  

There is no "none" to put the hash sign before. Could anyone say if I have to type none in as well.  

Thanks for any replies.


Hello Steve

---

### Post by HDTimeshifter on 2010-05-16
I commented it out, but when I rebooted, still got the error.

---

### Post by xisxas on 2010-05-18
After entering:  sudo nano /etc/fstab in the terminal, I put the # sign in front of the line that appeared in it: # usbfs/proc/bus/usb    usbfs   devgid=14 0 0, and I now no longer get this message on the screen when booting up:&quot;An error occurred while mounting /proc/bus/usb
Press S to skip mounting or M for manual recovery&quot;.


Hello Steve

---

### Post by jcblll on 2010-10-17
Worked for me after 10.04.4 upgrade.
Thanks,
jcb

---

