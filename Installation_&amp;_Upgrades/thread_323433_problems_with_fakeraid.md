---
title: "problems with fakeraid"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by blaublutig on 2006-12-22
Hi i tried installing feisty on a system with nv_raid
trouble is that after i installed the base sistem and 2 kernels 2.6.19-7-386 and 2.6.20-2-386
installed dmraid 1.0.0, configured grub.
when i boot each of the linux image
i get this: "no block devices found" :(  
Pls help.

---

### Post by tomm3h on 2007-02-16
How is grub configured?

If you can, could you get a copy of your menu.lst and device.map?

---

### Post by blaublutig on 2007-02-17
i have configured grub as in the fakeraid tutorial
and the entry in my menu.lst looks smt like this:
root (hd0, 6)
kernel /vmlinuz-2.6.19-7-i386 root=/dev/mapper/nvidia_iccaee8 ro 
initrd /initrd.img-2.6.19-7-i386

i have a boot partition and a root partition.

---

### Post by tomm3h on 2007-02-17
There are two FakeRaid tutorials, FakeRaidEdgy and FakeRaidHowTo. The latter's (fully manual) explanation works a treat, the former's isn't useful at all.

I'm assuming the latter, but unfortunately I'm no grub expert. My sole reasoning for pasting the device.map and menu.lst files was to see if there were any simple errors (I've been looking at those damn tutorials for weeks, heh)

Sounds like you've got it setup OK? Though might still be worth pasting the files in to make sure.

Have you run update-grub again after making a back-up of menu.lst and compared the two?

---

### Post by blaublutig on 2007-02-18
upgrade-grub does not set root correctly it set's it to (hd0,0) instead of (hd0,6) where /boot is.
and about the device.map file, it seems that i can't find it on my installation :( .

---

### Post by tomm3h on 2007-02-18
When trying to run grub-installer (even though it fails) it will create /target/boot/grub/device.map but with the wrong device (/dev/sda or so).

What you need to do is nano that file, and change it to /dev/mapper/your_raid_device.

Then run through the grub shell, and set the groot (or root = hd(0,6)) in the grub console. See [here]("https://help.ubuntu.com/community/FakeRaidHowto#head-dca939034096e9aaa1e3a5e77bbc419fc77a4417"). (That article had a much better explanation of setting up Grub via the shell, with dmraid.)

Follow that through and you should be OK to then edit menu.lst and run update-grub thereafter. :)

---

### Post by blaublutig on 2007-02-18
i did that before, and grub works (i can choose to boot in windows with no pb)
the problem is when i try to boot into linux than it gives me the error and stops.

---

### Post by tomm3h on 2007-02-18
> **blaublutig said:**
> i did that before, and grub works (i can choose to boot in windows with no pb)
the problem is when i try to boot into linux than it gives me the error and stops.

Which points in the direction of mis-configured grub. Hence why I was going over the steps of configuring grub and making sure you'd completed them correctly..

If at first you don't suceed, don't bother going back and checking what you've done because it can't be wrong? Doesn't sound like a fantastic methodology.

You've already said you don't appear to have a device.map. I don't know how you expect grub to know of your fakeraid array?

---

