---
title: "yet another not enough disk space 9.04 question.."
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by aaroncook5 on 2009-12-17
sorry to rehash all this yet again, but I've not found a fix for me yet..
[INDENT]I have an aspire one d250 dual booting win7 and 9.04UNR. I love it so far!!  The problem, as i'm sure you could gather, is that I'm unable to upgrade.  I've uninstalled/reinstalled 9.04, allocating 25gb for the UNR install, ran sudo apt-get clean/autoremove, and still my disk usage analyzer shows im using %100 of 17.3mb...  any advice would be greatly appreciated!


[/INDENT]

---

### Post by mikewhatever on 2009-12-17
Can you post the output of <df -h> without brackets to verify the situation.

---

### Post by aaroncook5 on 2009-12-17
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.0G  190M  92% /
tmpfs                1003M     0 1003M   0% /lib/init/rw
varrun               1003M   92K 1002M   1% /var/run
varlock              1003M     0 1003M   0% /var/lock
udev                 1003M  152K 1002M   1% /dev
tmpfs                1003M   88K 1002M   1% /dev/shm
lrm                  1003M  2.4M 1000M   1% /lib/modules/2.6.28-11-generic/volatile



so my question then is if i've allocated 25gb for UNR, why does it only see 2.3gb?  Did the installer partition this space out of the 25 and did i miss the option to set this space allocation during install?

---

### Post by mikewhatever on 2009-12-18
Apparently, something went wrong there. How exactly are you allocating the space?

---

### Post by aaroncook5 on 2009-12-18
during install from USB, i used the slider on the partition page to allocate the 25gb.  if it makes a difference, i selected "install side by side" as I'm dual bootin with win7

---

### Post by phillw on 2009-12-18
Hi

It's best to use the partitioning tools within Win to 'shrink' their areas - leave it as unused space. Then ensure your Win re-boots, frequently - Win wants to run a few disk checks.

Once Win is happy, use gParted to 'grow' your Ubuntu area from the 'free area'.
So, if you have already got a section of free space, use gParted to allocate it to your Ubuntu area.
Regards,

Phill.

---

### Post by mikewhatever on 2009-12-18
> **aaroncook5 said:**
> during install from USB, i used the slider on the partition page to allocate the 25gb.  if it makes a difference, i selected "install side by side" as I'm dual bootin with win7

Can you also post the output of <sudo fdisk -l> to verify there aren't multiple Linux partitions. If that's the case, we'll need to get rid of the redundant ones, but regardless of what went wrong, I think Phillw above is right, you don't need to reinstall. Just resize the already existing partition.

---

### Post by aaroncook5 on 2009-12-18
here's hoping this will format in some readable way once i post it..

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9a92f804

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1307    10489856    7  HPFS/NTFS
/dev/sda2   *        1307       19132   143180632    7  HPFS/NTFS
/dev/sda3           19133       19457     2610562+   5  Extended
/dev/sda5           19133       19435     2433816   83  Linux
/dev/sda6           19436       19457      176683+  82  Linux swap / Solaris


this is the part where i get in way over my head.  But I want to say thank you to you guys, this kind of support alone is worth the jump from the Redmond plank!

---

