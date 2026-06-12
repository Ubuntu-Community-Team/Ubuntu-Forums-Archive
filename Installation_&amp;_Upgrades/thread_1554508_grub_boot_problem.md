---
title: "grub boot problem"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by ktc0000 on 2010-08-16
I just installed ubuntu (dual-booting with Windows XP), and ive been  installing necessary programs and such.  i checked the "mark all  upgrades" button in Synaptics and let ubuntu do its thing.  after the  updates were complete, i was chatting on empathy and all of the sudden i  cant type....anywhere.  cursor was basically useless.  so i restarted  my laptop, and lo and behold, the following message pops up and the boot process goes no farther:

error: no such device: 7dabc3ea-74c2-4a53-bba3-f60d6271ffd1.
grub rescue>

Im at quite a loss as to what to do next, and any help would be greatly appreciated. thanks

---

### Post by oldfred on 2010-08-16
Can you boot from the rescue mode?

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

What partition is the error? From liveCD to see UUIDs:
sudo blkid

Did you edit any partitions before error appeared?

---

