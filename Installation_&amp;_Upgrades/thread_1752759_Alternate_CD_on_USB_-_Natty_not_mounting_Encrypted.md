---
title: "Alternate CD on USB - Natty not mounting Encrypted Volume"
date: 2011-05-08
forum: Installation &amp; Upgrades
---

### Post by jpcss on 2011-05-08
Alternate CD on USB - Natty not mounting Encrypted Volume

I get **initramfs** prompt.
[B][SIZE=2]
I have a Dell Inspiron Duo. 
I've tried to install Natty i386 and AMD64.
I set my / (root) and swap under LVM under an encrypted volume. [/SIZE][/B][SIZE=2]Used manual partitioning[/SIZE][B][SIZE=2].
But after reboot, I successfully enter the passphrase, swap and root are not mounted.[/SIZE][/B]

Now, I've had this working with 10.10. System seemed a little quirky after the upgrading it to Natty. So, I wanted a fresh install.

Used Unetbootin to run ISO from USB and also from one of my other partitions. I've tried installing at least 10 times, some repeat, some variations.

---

### Post by jpcss on 2011-08-25
It would not let encrypt the whole / (root). It works if I encrypt I just encrypt the /home directory and swap.
[INDENT][INDENT]         [SIZE=2]**Both ways I leave the /boot partition unencrypted**[/SIZE]
[/INDENT][/INDENT]

---

