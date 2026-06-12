---
title: "Major upgrade weirdness!"
date: 2008-07-08
forum: Installation &amp; Upgrades
---

### Post by gr8dogs on 2008-07-08
While I've used other flavors of unix/linux for a long time, only recently have I tried Ubuntu.  With only a couple of exceptions, it has been pleasant enough.  The major weirdness occurred when I clicked on the Update Mangler's option to "Upgrade" to 8.04 LTS. Everything appeared to go perfectly normally - it went through all the steps to upgrade without incident and then said it needed to reboot.  I let it reboot, and even though I had watched it configure a new kernel (2.6.24-19), after the reboot it came up with the same "2.6.22-15 generic #1 SMP".  Plus, the update manager still tells me that the  upgrade to 8.04 LTS is available.  

Just for grins, I told it to upgrade again.  It went through all the same steps.  Rebooted again, with the same results as before.  (I guess it's nice to know I hadn't hallucinated the first time.)  I looked at /boot/grub, and the latest changed file was several weeks old (for the 2.16.22-15 kernel)

Does the upgrade process leave any crumbs around to let one know what it thinks it has done?  The machine I'm trying to upgrade is a dual-core Intel  (ASUS P5E3 "Deluxe").  The only other previous weirdness I've experienced is that a couple of the packages I've previously installed seemed to have thought I was running an AMD 64-bit processor.

Any ideas why this upgrade fails would be appreciated!

Thanks ... Richard

---

### Post by Rallg on 2008-07-08
Sounds like the "automagic" update to Grub's menu.lst isn't working for you. I do not know why.

You can manually force Grub to boot to the -.19 stuff by editing the menu during boot. The edits are temporary, for the one boot. You can also manually edit the menu for permanence:

gksudo gedit /boot/grub/menu.lst

Does that work for you, or does your system still insist that it hasn't been upgraded, even after booting to -.19?

---

### Post by gr8dogs on 2008-07-08
> **Rallg said:**
> Sounds like the "automagic" update to Grub's menu.lst isn't working for you. I do not know why.

You can manually force Grub to boot to the -.19 stuff by editing the menu during boot. The edits are temporary, for the one boot. You can also manually edit the menu for permanence:

gksudo gedit /boot/grub/menu.lst

Does that work for you, or does your system still insist that it hasn't been upgraded, even after booting to -.19?
I neglected to point out in my original post that the new kernel isn't in the /boot directory, either.  I know I SAW messages about it before the reboot, but I have no clue where it put it.  (There is no corresponding vmlinuz file anywhere on the disk.)

Does the upgrade process write out any logs anywhere?

---

