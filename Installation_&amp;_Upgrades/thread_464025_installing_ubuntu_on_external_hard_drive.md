---
title: "installing ubuntu on external hard drive"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by ham in Maryland on 2007-06-04
I have a pc running Windows XP.  I want to run Ubuntu on an external hard drive.  What steps and pitfalls do I need to be aware of?

---

### Post by depele on 2007-06-04
there are already some forums of this topic.

once again

[LIST]
[*]attach you external disk (usb i assume)
[*]load the ubuntu live cd
[*]install ubuntu (make sure you install it on your external drive as it comes to partitioning)
[/LIST]

for installing grub you have to options.

1. ==> I have installed it on the boot record of the external drive. so everytime I want to boot from the external drive I have to go into my bios and set the external drive as first drive to boot from. But when I want to boot from my internal I get no grub. My computers boot configuration isn't changed.

2. ==> install grub on your internal drive. So everytime you boot, grub will show up. I am not sure what happens if you want to boot your linux when your external drive isn't connected.

booting from external drive gives a little latency as it comes for booting. 

I hope you are satisfied with this answer.

grtz..
and good luck

---

