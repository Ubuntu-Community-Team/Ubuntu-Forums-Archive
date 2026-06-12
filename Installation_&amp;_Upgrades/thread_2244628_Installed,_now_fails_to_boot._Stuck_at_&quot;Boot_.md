---
title: "Installed, now fails to boot. Stuck at &quot;Boot from CD/DVD:&quot;"
date: 2014-09-17
forum: Installation &amp; Upgrades
---

### Post by AwaitingUserInput on 2014-09-17
I have a computer with 2 hard drives:
64 GB SSD
500 GB regular disk drive

The 64 GB SSD used to be used as a Windows 7 cache drive. I mention this because there may be some remnants of a Windows bootloader on there, but I'm not sure how these things work, so I may be wrong.

During installation, on the SSD I created and formatted 1 partition as ext4, and did a manual install where I told it to use that drive as the "/" mount point. I also told the installer to put the bootloader on that drive when it asked where I want the bootloader.

On the HDD I formatted 1 partition as ext3, and made it the /home mount point.

I did not make a swap partition, as I plan to make a swap file and put it on the HDD after the fact.

Everything seemed to work but when I rebooted the computer I get the message, "Loading operating system..." Then "Boot from CD/DVD:" on the next line is a blinking cursor and the computer is stuck there.

Can anyone tell me what I may have done wrong and how to get my machine to boot into the OS?

---

### Post by AwaitingUserInput on 2014-09-17
I wound up booting to a live USB drive, installing boot-repair and just running that with all defaults left alone. My computer now works.

---

