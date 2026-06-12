---
title: "Where's Lilo?"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Muskiet on 2010-02-24
I want to install Ubuntu 9.10 64-bit from the alternate CD and I know I can use that to install Lilo instead of Grub.
The trouble is that nowhere in the installation I see the question "what bootloader do you want to install?".
It just installs Grub every time and apparantly that is not a very good choice for RAID systems.

---

### Post by jfparis on 2010-02-24
You need to complete the instalation with Grub first

Then you can install lilo with

```
apt-get install lilo
```

You might be better off removing grub too after that.

---

### Post by Muskiet on 2010-02-24
> **jfparis said:**
> You need to complete the instalation with Grub first

Then you can install lilo with

```
apt-get install lilo
```You might be better off removing grub too after that.

Here's what I don't get though... I've had the installation of Grub failing once due to me doing a bad setup with partitions and up popped a selection menu with the "install lilo instead" option while still in the installation part.
Now in that instance neither Grub nor Lilo could be installed, but I can't see why I can't get that same popup BEFORE it tries to install a bootloader?

Thank you for your answer, but I do think I should be able to install Lilo with the alternate CD, every documentation I've read so far says I can, but nowhere does it get explained as to how to go about it.

---

### Post by Muskiet on 2010-02-25
Never mind y'all, I've figured it out yet again by myself.

When the installation CD boots I have to hit F6 and choose "Expert Mode" before hitting the "Install Ubuntu" option.
I have to go through a lot of crap to install the rest of Ubuntu, but it will let me choose between Lilo or Grub.

---

### Post by chuina on 2010-02-25
Ohhh, **lilo**. I thought **dilo**,web browser. :o
Never mind.

This is a very good thread except mine post.

---

