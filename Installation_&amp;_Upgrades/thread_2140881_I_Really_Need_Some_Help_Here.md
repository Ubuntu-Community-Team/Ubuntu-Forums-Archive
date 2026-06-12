---
title: "I Really Need Some Help Here"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by CharleyGnarlyP290 on 2013-04-30
I installed 13.04 on my computer (about 1.5 years old.) When the install finished the DVD drive drawer opened up and I got the message to remove the disk and reboot, so that's what I did.
The computer started to reboot, but all that came up was a black screen. I let it sit for quite a while to see if it would do anything, but nothing. I then turned the computer off and restarted it. It boots right up to Windows 7 with no option to choose between Ubuntu or Windows.
What do I do? I have searched the web over and these forums, but can't find an answer.
Thanks.

---

### Post by darkod on 2013-05-01
If it boots directly into windows, the grub2 bootloader wasn't installed successfully. Do you have uefi system or not?

Use boot-repair in live mode to make the boot info report and post the link here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

That will allow us to see more details.

---

