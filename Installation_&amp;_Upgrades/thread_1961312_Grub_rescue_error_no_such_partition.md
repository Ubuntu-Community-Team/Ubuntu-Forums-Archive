---
title: "Grub rescue error: no such partition"
date: 2012-04-19
forum: Installation &amp; Upgrades
---

### Post by nufail on 2012-04-19
Hi dears,

I have both windows 7 and ubuntu in my 'emachines' notebook.when I was working there was power failure and I hibernated the system. After restarting it's showing "error:no such partition", and prompts " grub rescue>" . I seek help from you all to fix this problem.

Note: 1. No CD drive in it.

      2. I din't remove any of the OS

Thanking you

---

### Post by darkod on 2012-04-19
How did you install ubuntu, with a usb stick?

Try to boot it from a usb stick into live mode (Try Ubuntu), and check which one is the linux partition with:
sudo fdisk -l (small L)

It can be for example /dev/sda5 (change the number 5 with the correct one according to your results).

Then you can run a check on the partition in case it was corrupted during the power failure. Also, why did you hibernate, why not shut down?

The check is run with:
sudo fsck /dev/sda5

---

### Post by ajgreeny on 2012-04-19
Did you boot into windows after hibernating your ubuntu system?  If you did that you may have corrupted your ubuntu; you must always close down completely before starting the "other" OS on a system.

---

