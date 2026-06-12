---
title: "Hardy doesn't work with VAIO??"
date: 2008-06-12
forum: Installation &amp; Upgrades
---

### Post by dmendizabal on 2008-06-12
I did a fresh install of Hardy in my laptop (Vaio VGN240) and it was a completely disaster. I've been using Gutsy before and everything worked well, but now I had to disable the ACPI (to start booting), my external mouse doesn't work, no possible to change the brightness, sound doesn't work and who knows what else I will find out later.

I've tried using other Kernels, I downloaded (kernel.org) and compiled 2.6.25 and 2.6.25.5 none of them worked well.
I've upgraded to 2.6.24.18 from Hardy-Proposed : Didn't work
I've even downloaded the kernel from Gutsy (2.6.22.14) from packages.ubuntu.com : No luck

Can anybody tell me if there is a possibility to sort this problem out or I will just have to go back to Gutsy??

---

### Post by iaculallad on 2008-06-12
Try to search your laptop model in [here]("https://wiki.ubuntu.com/LaptopTestingTeam") if it has been tested by the Ubuntu Laptop Testing Team Community.

---

### Post by dmendizabal on 2008-06-13
Finally I realized that booting in Recovery mode work perfect.
So, what I did was compare in the /boot/grub/menu.lst file the difference between the lines for Normal booting and Recovery booting. Making a try and error test, I deleted the acpi=off and quiet. Now everything works PERFECT.

The original line was:

/boot/vmlinuz-2.6.24-16-generic root=UUID=6fd0ee0d-21a3-45a9-9ab2-c6a31b651fb4 ro quiet splash acpi=off

The final line is:

/boot/vmlinuz-2.6.24-16-generic root=UUID=6fd0ee0d-21a3-45a9-9ab2-c6a31b651fb4 ro splash

I don't know what does it mean, but it works. Can anybody tell me if I'm doing something wrong deleting "quiet" ??


Things that weren't working before and they are working now:

Sound
External mouse
Suspend
Hibernate
Dial up

It is great!!!!!

---

