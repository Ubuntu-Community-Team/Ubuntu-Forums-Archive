---
title: "Incomplete bootup after upgrade to edgy"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by morpheus5 on 2006-10-29
I was using ubuntu 6.06 LTS, after upgrade, i attempted to reboot, but it doesn't bootup and i got stucked in kernel bootup.(Both 2.6.15 and 2.6.17-10-generic, with respective initrd image)
it was stucked in the /scripts/init-bottom line, it does not process into INIT what can i do now?

---

### Post by pablogabriel on 2006-10-29
The same happens to me. I've tried the noapic parameters on the kernel, I've tried renaming the partition on the kernel... nothing works. Did you solve it?

---

### Post by gario on 2006-10-29
I don't know if this will help, and if you're not very comfortable mucking with the command line and manually mounting filesystems you may not want to try this.  There maybe be an easier fix, but this worked for me.

In my case it looked like the update manager had quit in the middle of the process and rebooted while leaving most of the packages unconfigured.

I was able to boot by bypassing the regular init process and using bash instead.  If you go into the grub menu during boot, and edit the default boot entry (press "e" to edit the entry).  Then edit the "kernel" line (press "e" again) and append:

init=/bin/bash

This will execute bash as your init process instead of upstart.  Once you get the bash prompt, you can remount your root filesystem read-rewrite:

mount /dev/<your root partition> / -o remount,rw

Then I had to run "dpkg --configure -a" to complete configuration of the installed packages.

I don't know if this is the same problem as you are seeing, but at least the "init=/bin/bash" trick may get you into a prompt where you can further diagnose the issue.

Hope this helps.

---

### Post by bald_br on 2006-11-01
Gario,
that worked for me. Actually I also had to change the PATH but, after those steps a could complete the Edgy install. 
Thanks a lot.

---

### Post by h6w on 2007-01-07
This worked for me, too.

For the record, I typed:
export PATH=/bin:/sbin:/usr/bin:/usr/sbin
before the dpkg command

---

### Post by jhineman on 2007-04-13
Hmmm.  My machine is also hanging after an upgrade to edgy.  However, when append "init=/bin/bash" as suggested, I get a prompt (root@(none):/#) but I can't type anything!?

Any suggestions?

---

