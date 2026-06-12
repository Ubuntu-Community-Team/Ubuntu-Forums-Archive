---
title: "Reinstall Ubuntu studio"
date: 2015-11-30
forum: Installation &amp; Upgrades
---

### Post by Jan_Erik on 2015-11-30
Hi
I have  installed Ubuntu Studio Trusty Tahr 14.04.3 on a laptop and as a new starter I have been tweaking all sorts of settings in order to learn the system. However I want to start over with a fresh install. I assumed it would be OK to remove the HD from boot startup and force the boot sequence to select the Ubuntu DVD and format the disk as part of the reinstall. But when doing this nothing happens and I only get a black screen and no action and the DVD stops spinning after a few seconds. 

I then downloaded the application "disks" and tried to select format here but I get an error because the disk is obviosly mounted since I am logged in to  Ubuntu.
Error unmounting /dev/sda1: Command-line `umount  "/dev/sda1"' exited with non-zero exit status 1: umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
 (udisks-error-quark, 14)

So my question then is what is the best process for reinstalling a fresh Ubuntu studio?

Thanks

---

### Post by Bucky Ball on 2015-11-30
*Thread moved to **Installation & Upgrades**.*

Switch off the computer (if you are going to use a DVD to install you may need to put that in first). Plug in the install media (USB or shove in the DVD prior to shutdown)> boot the machine to the BIOS or boot device menu (the key for BIOS varies, F12 is a common one for a boot device list) and set to boot from the install media.

If you get that far and you want to reinstall, choose the 'Something Else' option when you get to the partitioning section of the install and manually partition, install in the partition you have Ubuntu installed in currently.

---

### Post by Jan_Erik on 2015-11-30
Thanks! I am writing this from a fresh installation. I used the method as you described and it worked fine. However after selecting boot as a DVD ubuntu started in test/portable modus but I got the option to install and format the disk after Ubuntu"test" had started.

If I wanted to  manually format the disk can I please ask you to advise if you know the best way to do this?

Thanks

---

### Post by grahammechanical on 2015-11-30
Run the Live - Try session and open the Disks utility or Gparted. The Ubuntu Studio Try session may not have the Disks utility installed as it is Gnome software but it surely has Gparted.

Regards.

---

### Post by Bucky Ball on 2015-11-30
As above. Boot to a live Session (Try Kubuntu) and open Gparted (which is on the install disk). Resize partitions. 

... but you say 'manually format'. Do you mean manually partition? You can do that at 'Something Else' when you're installing, but now installed, yes, live session if you want to make changes.

---

### Post by Jan_Erik on 2015-12-01
Thanks for all good advise :)

---

