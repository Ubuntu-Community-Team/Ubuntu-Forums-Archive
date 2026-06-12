---
title: "Installing on external hard drive"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by petersohn on 2010-03-14
My situation is the following: I have a laptop which has Windows installed on its internal hard drive, and I don't want to change its configuration. I want to install Ubuntu on an external hard drive, then set in the setup to use it as the first boot device, so it will only boot Windows if I unplug the external HD.

I tried it with Ubuntu 9.10 on a pen drive. I booted from the CD and partitioned the pen drive (/dev/sdb) to install on it. After rebooting, I saw that it installed Grub onto my internal hard drive instead, which in turn couldn't boot if the pen drive was not plugged in (because /boot was on the pendrive), and it also couldn't boot if it was plugged in (unsure why). So I had to restore the MRB of my HD.

Any ideas?

---

### Post by nah40 on 2010-03-14
One way is to remove the windows drive, intall the other one, intall Ubuntu, then remove and re-install the Windows drive.  Ubuntu will run from the USB connection if the laptop is set to boot from USB. This will not affect windows.

---

### Post by petersohn on 2010-03-14
Since I don't want to tamper with the insides of the laptop, I don't think that I want to unplug my hard drive.

Question: If I install Ubuntu on another machine (for example on my desktop, which has its HD in a rack anyway), will it run on another machine, such as my laptop? I know Windows doesn't like if you want to run it on another hardware. What about Linux?

---

### Post by nah40 on 2010-03-14
If grub is installed on it, it should work.
I have switched the drive in my laptop many times to try other systems with no problems

---

### Post by petersohn on 2010-03-14
Thanks. Then I will try it that way.

---

