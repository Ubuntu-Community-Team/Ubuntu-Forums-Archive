---
title: "Installation but won't boot"
date: 2008-06-04
forum: Installation &amp; Upgrades
---

### Post by WaitingforGuiteau on 2008-06-04
Hi all,

I recently installed Ubuntu on a 250 GB hard drive in my computer, while a barely functioning copy of Windows XP and a completely blown (GRUB error) Fedora 9 sits quietly on a 120 GB hard drive. I popped in the Ubuntu Install CD, went through the process on the 250 GB hard drive, no problems, restarted, went into the BIOS and set the 250 GB hard drive to be the first disk to boot from, and...nothing. My computer displays the first two CD boots which does nothing, then just hangs up. It doesn't freeze or anything like that, it just doesn't do anything.

Is this a common problem? Do you need more information? Thanks for your help.

---

### Post by Pumalite on 2008-06-04
Boot your Live CD and post:
sudo fdisk -lu

---

### Post by WaitingforGuiteau on 2008-06-05
Thanks, I'll do that tomorrow when I get home from the office. The many joys of working at a national lab...

---

### Post by WaitingforGuiteau on 2008-06-05
okay, I don't have Internet on my desktop so I'm posting the big results from my phone. It listed the two hard drives, sda with the Ubuntu partitions, and sdb with seven (two for windows, four or so for Linux and solaris, and one with a few letters that I didn't recognize). The one I didn't recognize, which is on the smaller hard drive, was the only one with an asterisk next to it under the column labeled boot.

I tried installing a boot loader onto sda but that did not solve the problem.

---

