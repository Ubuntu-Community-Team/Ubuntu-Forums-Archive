---
title: "add swap in an encrypted drive"
date: 2020-04-11
forum: Installation &amp; Upgrades
---

### Post by kaky951357 on 2020-04-11
Hello folks,
I recently installed Ubuntu on my computer and i choosed to encrypt all the partition, unfortunately i forgot to add a swap partition so now my system don't want to wake up after being suspended.
I use ubuntu 18.04 in a dell latitude 7490.
Can i add a swap partition in my system, if yes can someone tell me how ? will it be easier to just reinstall all the system ?
stay safe and have a great day.

---

### Post by lvm on 2020-04-12
It is not necessary to use a dedicated partition for swapping, you can use plain file(s) for that. Not sure whether it'll work on an encrypted device, but at least you can give it a try before doing anything more drastic. Swap files are created with mkswap, managed with swapon and should have entries in /etc/fstab if you want swapping to start automatically on boot. Multiple files are ok. Shrinking filesystems and then partitions to make space for swap partition might be possible (not sure that all filesystem types support shrinking but most common ones like extN do) but slightly more risky, you must be extra careful not to shrink the partition more than you shrank the filesystem - there are no checks at this stage, not with standard tools anyway.

---

### Post by CelticWarrior on 2020-04-12
Not only the swapfile is already there, automatically created and used, swap or the absence of it has nothing to do with suspension issues. Suspension happens exclusively in RAM. Hibernation - not suspension - is what needs swap.

This is a X-Y problem.

---

