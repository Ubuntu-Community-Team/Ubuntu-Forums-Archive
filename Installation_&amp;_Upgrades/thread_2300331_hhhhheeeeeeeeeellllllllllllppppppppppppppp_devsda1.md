---
title: "hhhhheeeeeeeeeellllllllllllppppppppppppppp /dev/sda1 deleted"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2015-10-25
By accident I have deleted  my /dev/sda1  so ubuntu can not boot is it possible to restore it ?
I am desperated

---

### Post by westie457 on 2015-10-25
It might be possible to rescue this.

Tools needed. A LiveDVD/USB to boot into 'Try Mode'

When in Try Mode open a terminal and enter the following commands one at a time ```
 sudo apt-get upddate
sudo apt-get install testdisk
sudo testdisk
``` Follow the on-screen prompts. The default selections usually work just fine.

If not sure check this for guidance [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

---

### Post by grahammechanical on 2015-10-25
If sda1 was the Ubuntu partition then the best you can hope for is to use testdisk to recover important data before re-installing Ubuntu.

If sda1 was the boot partition, then you may not have lost your Ubuntu installation. You could use Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This will produce a report and store it in Pastebin and give you a URL. Add the URL to this thread so that we can see the situation as it is. At the bottom of the Boot Repair report you will see a recommended repair option. That recommended repair option is important.

You might choose to not accept the offer to carry out the recommended repair until others on this forum have had an opportunity to give advice based on the Boot Repair Report. It also makes a difference if the machine has a BIOS or a UEFI boot system and what other OS is on the machine.

Regards.

---

### Post by oldos2er on 2015-10-25
> **hoboy said:**
> By accident I have deleted  my /dev/sda1  so ubuntu can not boot is it possible to restore it ?
I am desperated

What file system was on /dev/sda1?  Restore from snapshots or backups? Is this a dual boot system? I'm assuming sda1 was your root partition, is this correct?

---

