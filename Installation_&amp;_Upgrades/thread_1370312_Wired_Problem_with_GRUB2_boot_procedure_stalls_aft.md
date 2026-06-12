---
title: "Wired Problem with GRUB2: boot procedure stalls after grub menu"
date: 2010-01-02
forum: Installation &amp; Upgrades
---

### Post by mdatab on 2010-01-02
Hello,

on my new HTPC, I've installed Ubuntu 9.10. I'm using SW-RAID1 for /boot and the rest is SW-RAID5 with LVM. My problem is, that most times (not always) the boot procedure stalls grub selects the default menu entry. After that, I only see a blank screen with a blinking cursor on the upper left. This state seems to last forever until I press any key on the keyboard (which is a mess since I don't want to have a keyboard attached to this computer). 

What is the problem here? :confused:

Thanks a lot
Martin

---

### Post by mdatab on 2010-01-03
After replacing GRUB2 with GRUB1 the problem **is still there**. Sometime the machine boots, sometimes I have to hit a key.

Do you have any ideas?

---

### Post by ratiafak on 2011-01-07
I have the same problem. I have server which stucks in grub unless I have a keyboard connected. I've figured out that bios sends some sort of warning and then grub won't start.
You can connect PCB cut from old keyboard.
What bothers me is that server sometimes won't boot after power-loss and I have to manually press enter with another keyboard. Anyone know how to set grub to boot always?

---

