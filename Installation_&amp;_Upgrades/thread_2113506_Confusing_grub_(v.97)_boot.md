---
title: "Confusing grub (v.97) boot"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by andyinor on 2013-02-07
Hi. . . this is really confusing.  I'm not a linux newbie but I don't get too far into the weeds (which might be the worse possible combination:-)

I recently added a second hard drive that came from a OneBook NAS device that was running BusyBox.  Now when I reboot, it insists on booting from that (new) drive rather my (original) drive.  

[LIST]
[*] The BIOS is selected to boot my original drive
[*] Grub is setup to use the original drive by default (this is the main thing that seems to not be working)
[*] If I go into Grub (c)ommand line) and manually specify the SAME root drive, root partition, and kernel as is in the default boot configuration, it WORKS!
[*] But if I just let Grub load the default (which has all the same information I use when starting manually), then it goes back to the new drive and the busybox configuration.
[/LIST]

To make it worse, I use a wireless keyboard which apparently doesn't have enough mojo during the boot process to break into the Grub menu so right now I have to have a second keyboard plugged in so that I can interrupt and go into the manual boot command line.

Any ideas??

Andy

---

### Post by darkod on 2013-02-07
I don't understand exactly what is the problem honestly. :)

But if you can boot at least once with any manual commands, simply install grub2 to the new disk also, and case closed. Even if the machine insists on booting from it, it will work. In terminal just do (depending if the new disk is sda or sdb):
sudo grub-install /dev/sda

Note, the above doesn't work from live mode, only from the booted installation.

If you need to do it from live mode just say so.

---

### Post by andyinor on 2013-02-07
Thanks, Darkod.  I didn't think of that and I think it would work, though somehow it seems like a hack since I should only need grub in one place.

What is odd is that the grub boot menu does appear so apparently it's loading the correct MBR from /dev/sda.  But after selecting the desired boot option, it flips over to /dev/sdb to load the old busybox.

---

### Post by darkod on 2013-02-08
Correct, you need grub2 at minimum on one MBR, as long as you can select to boot from that disk.

If in this case your computer is misteriously not letting you boot from the intended disk, there is nothing wrong having grub2 on the MBR of all disks. It will still be "connected" to the same grub.cfg file, there is only one of them. The MBR part is simply small code that tells it to jump and use grub.cfg.

---

