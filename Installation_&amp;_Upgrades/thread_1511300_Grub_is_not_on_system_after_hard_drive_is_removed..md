---
title: "Grub is not on system after hard drive is removed."
date: 2010-06-16
forum: Installation &amp; Upgrades
---

### Post by European bob on 2010-06-16
I have 6 hard drives that have 9.10 and 10.04 on them.  Not as a dual boot, but some hard drives have different versions on them.  When I have plugged the drives in a couple of weeks later, the grub is gone and system will not boot.  I get like a grub 1.5 error and that is all the options I have.  Does anyone one know why this happens?  Nothing on the drives but the O/S to get rid of windows.  All drives worked perfect until they were removed and installed later.  I am a newbie.

---

### Post by darkod on 2010-06-16
The boot process obviously doesn't flow the way you expect it. With 6 disks you have to make sure where is grub installed, from which ubuntu version, and which disk is the first you are trying to boot from.

You can try to boot from another disk in BIOS, or for more detailed information just run the boot info script as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by European bob on 2010-06-16
What I mean is that I have 6 discs with operating systems on them.  I only run 1 disc in a machine.  I had upgraded to ssd drives and came across my old sata drives.  When I plugged it into the same pc that it worked on a couple of weeks ago, it would not boot and gave me the grub error.  It almost seems like it how the cmos works or resets itself when the battery on the motherboard is bad.  I figured it worked before and nothing changed other that me taking it out of the machine and placing it on a shelf

---

### Post by oldfred on 2010-06-16
Yes but do you still have your SSD plugged in?

Run the script with the drive(s) plugged in. And then we can see if you have something set by drive number not by UUID.

---

