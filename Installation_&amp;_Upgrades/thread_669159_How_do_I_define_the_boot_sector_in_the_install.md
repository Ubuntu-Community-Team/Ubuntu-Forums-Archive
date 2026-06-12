---
title: "How do I define the boot sector in the install?"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by mikey2gorgeous on 2008-01-16
Hi all,
   I'm installing Ubuntu on my IDE0 slave drive. i have a /boot partition of 50 Mb, then / & swap parts. These are mentioned as hda6 for example by the partitioner.
   When the install gets to page 6 & there's the 'advanced' tab I want to specify the boot sector I have created so grub isn't installed over my Windows loaded in the MBR on hda0. The option shown in the box is hdb0. The install fails at the grub install point with this option. What should I be putting in the advanced bit to specify the boot sector?
   Do I need a separate boot sector at the start of the disk? if the first partition is the / one?

regards

Mike Chalkley :)

---

### Post by Pumalite on 2008-01-16
A boot sector is for very particular purposes. You can do just fine with '/'

---

### Post by mikey2gorgeous on 2008-01-16
Great - I'll reformat that space back in then..

On the other question - am I having trouble because I'm trying to install grub on a slave drive? Does it have to be master drive on the secondary IDE to work?

Mike

---

### Post by Pumalite on 2008-01-16
Nope. But if you have Windows, then Windows has to be sda

---

### Post by nero_86 on 2008-01-16
You can install grub on the /boot partition. The win loader will be replaced on the MBR whit the grub loader. But grub perfectly recognise the win os and automatically add the win entry when starting the computer.

---

