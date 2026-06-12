---
title: "grub2 boots windows vista into the recovery partition"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by late_adopter on 2010-06-19
Good day,  [I]installed Ubuntu 10.4 onto an HP DV2 1030/Vista laptop after creating a partition for it.  Grub2 appeared on reboot and boots linux fine, but sends me to the recovery partion if I try to boot Vista from Grub2.  Used Bootrec to reinstall window loader and the Vista installation is Ok.  Reinstalled Grub2 using instuctions from the Ubuntu site but Grub 2 still sends me to the Recovery partition when I try to boot Vista.  Happily, I can reset the Vista boot up easily from the recovery partition.

I suspect I need to edit Grub2 to point the Vista choice to the right place, but how ?
[/I]

---

### Post by darkod on 2010-06-19
Grub2 just detects boot files and tries to guess which OS they are from. The recovery partitions actually have boot files resembling vista or 7.

But you should also have the boot files of your vista installation detected too.

To see details what is where, you can download the boot info script from my signature and run it. The results file will have a lot of details about the boot process and the boot files. If you need instructions how to run it:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by pastalavista on 2010-06-19
Are you using 64-bit Ubuntu? The one box I run 64-bit has the Vista grub entries backwards. If I select the Vista loader, it boots recovery but if I select recovery, it boots into Vista. I haven't figured out how to fix it, so I plan to install 32-bit Ubuntu soon as I get time. 64-bit Ubuntu isn't ready for prime time.

---

### Post by darkod on 2010-06-19
> **pastalavista said:**
> Are you using 64-bit Ubuntu? The one box I run 64-bit has the Vista grub entries backwards. If I select the Vista loader, it boots recovery but if I select recovery, it boots into Vista. I haven't figured out how to fix it, so I plan to install 32-bit Ubuntu soon as I get time. 64-bit Ubuntu isn't ready for prime time.

I would be surprised if grub2 from 32bit version detects them differently. I guess it comes down to how the boot files are detected.

If you want to change them, and you don't mind the os-prober disabled (you don't install new OS to search for every day I guess), you can open /boot/grub/grub.cfg and copy the two vista entries exactly as they are, to avoid typing errors, and paste them in /etc/grub.d/40_custom.

After pasting them change the titles in 40_custom as you wish. Save and close the file.

To disable os-prober and prevent doubling of the vista entries (once from the custom file and once from auto detection), run:

sudo chmod -x /etc/grub.d/30_os-prober

To update grub.cfg run:

sudo update-grub

It should boot correctly after that. Don't forget that os-prober is disabled and if you install new OS update-grub won't detect it.

You can always enable os-prober back with the command above only changing -x to +x.

---

### Post by pastalavista on 2010-06-19
Thanks, Darko. I'll do that.

---

### Post by drs305 on 2010-06-19
Here is a concurrent thread also started today dealing with the same problem. Some workarounds are presented and the OP may be talking to the devs about this issue.

[Grub mixes up menu entries in 10.4]("http://ubuntuforums.org/showthread.php?t=1513374")

---

### Post by late_adopter on 2010-06-19
Thanks guys,  

This gives me some ideas.  Likely I will delete the recovery partition as I have a recovery disc.  If I screw this up, I'll be back. I really want this to work.

---

