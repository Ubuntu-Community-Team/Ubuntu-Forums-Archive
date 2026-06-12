---
title: "Ubuntu on HDD, but GRUB on USB"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by blnl on 2013-01-01
I would like to install Ubuntu 12.04 on my notebook, but little differently than most of you.

My requirement is to have the Ubuntu installed on HDD, but the GURUB installed on USB key. Ubuntu will start only when I insert the GRUB containing USB key. Without the USB key Windows 7 will start.
Is this possible? And how to do it?

The idea is that there is no boot selection at startup, so from outside no one should notice that Ubuntu is installed on this machine.

---

### Post by darkod on 2013-01-01
You will have to use the manual installation method (Something Else), not the auto methods.

The manual install offers you total control of the partition sizes and where to install the bootloader.

---

### Post by blnl on 2013-01-02
Thanks darkod,

I did as you said and it works :)

Sometimes a solution is so simple that it seem unbelievable. Probably because I've been to much exposed to MS Windows.

---

### Post by darkod on 2013-01-02
Yeah, I like the flexibility of linux. You can't make windows install the bootloader where you want it. It always thinks it knows better than you. :)

Please mark the thread as Solved, it helps other people. You can do that in Thread Tools above the first post.

---

