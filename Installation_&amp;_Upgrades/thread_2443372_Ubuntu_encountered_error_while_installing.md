---
title: "Ubuntu encountered error while installing"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by digital-junkie on 2020-05-14
I encountered an issue installing Ubuntu 20. While installing it this is the error that comes up.

"The installer encountered an error copying files to the hard disk 

[Errno 5] input/output error"

I thought the issue was from the flash, I have changed up to 3 flash, it still didn't work out. I don't know what next to do, I have tried it severally.

Please help

---

### Post by CelticWarrior on 2020-05-14
The error is in the hard disk, clearly.

---

### Post by digital-junkie on 2020-05-14
Please how can I solve this?

---

### Post by CelticWarrior on 2020-05-14
Replacing the drive.

---

### Post by oldfred on 2020-05-14
I would check smartstatus on hard drive.

From Ubuntu you can use Disks and in upper right corner icon is SmartStatus.
While it can run many drive checks all I know is that it can say good or bad on drive.

Post this from live installer:
sudo parted -l

---

### Post by CelticWarrior on 2020-05-14
An hard drive failure is entirely expected as mentioned in this final comment on a thread where LOTS of problems were found, including file corruption: [https://ubuntuforums.org/showthread.php?t=2442291&page=2&p=13953124#post13953124](https://ubuntuforums.org/showthread.php?t=2442291&page=2&p=13953124#post13953124)

---

### Post by digital-junkie on 2020-05-14
I did a check on the hard-drive it reported. 

Smart check: PASSED
Smart DST: PASSED

---

### Post by digital-junkie on 2020-05-14
I had formatted the harddrive while installing Ubuntu 20

---

### Post by CelticWarrior on 2020-05-14
> From Ubuntu you can use Disks and in upper right corner icon is SmartStatus.
While it can run many drive checks all I know is that it can say good or bad on drive.

Please try the short test first and even if it still says "OK" try the extended one next (this will take a very long time).
Whatever test you did is rubbish. What takes 5 minutes to check a drive is worthless.

---

