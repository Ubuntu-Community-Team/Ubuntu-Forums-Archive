---
title: "Cannot read my previous RAID"
date: 2011-09-24
forum: Installation &amp; Upgrades
---

### Post by fossilman on 2011-09-24
Hello,

First of all I must declare that I am a completely idiot related to Linux, if you are so kind to answer my questions, please do it assuming that I know nothing at all of what you are talking about.

I decided to give it Linux a try and did some research about distributions and choose Ubuntu, in this very forum I read some guy saying that the best option to install Ubuntu is in a separate disk if you want to do a dual boot, disconnect it and then reconnect it after the installation is made.

I have 6 HDD´s of 1TB each, one disk running MS Windows 7, 4 disks in a RAID 5 (the BIOS is running it), and the last one, which was a spare disk, I used to install Ubuntu 11.04, I disconnected all the other HDD's and installed the OS, everything was smooth and had no problems at all, and after finishing the installation I ran "sudo update-grub" and now I have real dual boot.

I can see all my partitions EXCEPT, the RAID 5 which is nowhere to be seen. I read must of the documentation and must of the emphasis is to make a new RAID, I saw nothing related to see a previous installation, I read something about Ubuntu can work with all FakeRaids (as they call it), but how I can see even the system files of Win 7 and cannot see my RAID?

Any help will be appreciated, and please refer to the first paragraph for your answers.

---

### Post by Quackers on 2011-09-24
If you're using 11-04 try installing the kpartx package via synaptic package manager then check to see if the raid array is shown.

---

### Post by fossilman on 2011-09-24
> **Quackers said:**
> If you're using 11-04 try installing the kpartx package via synaptic package manager then check to see if the raid array is shown.

I installed the kpartx and then reinstalled it, and still not working at all, (assuming that I am running it correctly)I cannot see my RAID:

All that I receive is:

> /dev/mapper/control: open failed: Permission denied
Failure to communicate with kernel device-mapper driver.


REMEMBER, I have less that 24 hours using Linux, try to be specific with your answers, do not assume that I have a knowledge that obviously I do not possess.

---

