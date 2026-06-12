---
title: "BUG: soft lockup"
date: 2009-09-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Haegin on 2009-09-12
Hi,

I've been running Karmic on my server for over a month with no major problems until today when I tried to connect to the computer to find it wasn't responding. I rebooted it and it didn't come back up.

Plugging in an external monitor showed GRUB was having issues and the Super GRUB CD didn't seem to be able to fix them (thinking about it I'm not sure it supports GRUB 2 yet).

Eventually after resetting the BIOS it booted again and seemed to work okay until it started checking my drives. It seemed to finish but started giving errors saying the following:

BUG: soft lockup - CPU#0 stuck for 61s [fsck.ext3]
BUG: soft lockup - CPU#0 stuck for 61s [fsck.ext3]
BUG: soft lockup - CPU#1 stuck for 61s [dhclient]
...

This went on and I rebooted. The next time it booted it gave me errors about "Code: Bad RIP value." then told me it was fixing it but needed to reboot to fix it. This I did and was rewarded with it rebooting several times before it successfully booted to the login prompt with an error output and a call trace part way through the boot process.

Logging in seemed possible but it never got to the shell prompt, instead it gave a BUG: soft lockup - CPU#1 stuck for 61s! [landscape-sysin:3209] error followed by another stack trace. This it repeated every 61 seconds. I rebooted. It soft locked even sooner.

Does anyone have any idea of a) how I can fix this and get my system back in to a working state or b) why this is happening and what I can do to prevent it in the future? All the hardware is pretty new but the PC has been running 24/7 for about a month.

---

### Post by Haegin on 2009-09-13
Just an update with more symptoms/problems. Apt is segfaulting either at the end of the update process or as soon as I run another apt command. I believe this is when it is accessing the apt database. Running strace -c apt-get update shows the following failures:

```

Syscall        Errors
^^^^^^^^^^^^^^^^^^^^^
open           22
stat           25
access         8
unlink         5

```

All other calls are fine. I'm now wondering if it could be the root partition which is having problems as the syscalls are all to do with reading files.

---

### Post by Haegin on 2009-09-13
Sorry for the triple post but I removed the /var/cache/apt/*.bin files to sort out apt and have updated the BIOS on my motherboard and currently the system seems fine. I'll mark this as solved for now.

---

### Post by CHaoSlayeR on 2009-10-19
^^ Thanks for the BIOS update suggestion!

That was the one that caused a similar issue with KVM at my machine.

C]-[aoZ

---

### Post by VMC on 2009-10-19
> **Haegin said:**
> Sorry for the triple post but I removed the /var/cache/apt/*.bin files to sort out apt and have updated the BIOS on my motherboard and currently the system seems fine. I'll mark this as solved for now.

Thanks for this. I ran across someone else removing the *.bin files after getting segmentation faults, and were then able to resume successful updates.

---

