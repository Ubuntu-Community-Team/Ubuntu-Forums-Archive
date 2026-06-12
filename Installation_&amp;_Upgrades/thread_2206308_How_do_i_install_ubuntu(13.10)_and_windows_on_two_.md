---
title: "How do i install ubuntu(13.10) and windows on two separate drives?"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by hina2 on 2014-02-18
I'm a noob to ubuntu and just tried to divide partition matually into swap,home,root,boot on /dev/sda (windows 7 was already on /dev/sdb) and got an error message at startup.
i'm using SSD as my main drive and HDD for storage so ubuntu will go to sda and windows 7 to sdb. how can i use those two on two separate drives and will it ask me to choose between two as it did when i installed them on a single drive? Thank you.

---

### Post by grahammechanical on 2014-02-18
What did that error message say. That would be useful so as to avoid it happening again.

You could try disconnecting sdb (Windows 7) and then installing Ubuntu and choose Use the Entire Disk option. Then there will not be any chance of installing Ubuntu to the wrong disk.

After installation and rebooting and testing the Ubuntu Install, reconnect sdb and reboot. Grub will not give you an option to load into Windows 7 because it does not know Windows 7 is there. That can be fixed.

Once back into Ubuntu open a terminal and run

```
sudo update-grub
```

and watch the output and see if Grub's os-prober detects Windows 7. Then run

```
sudo grub-install /dev/sda
```

Then Grub should give you an option to load Windows 7. You will also be able to change the boot priority in the boot system (BIOS) and boot into Windows that way but Windows will not give you an option to load Ubuntu.

Regards.

---

