---
title: "Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible."
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by mintyBrain on 2013-12-09
Hello Ubuntu forums,

I have recently installed xUbuntu alongside Win7 on a diff partition.
Now, my problem was that GRUB did not boot, so I installed it on my Starting partition.
But then, when i tried, i got an error saying:
```
Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```
I mounted /dev/sda1 (my starting partition) as /mnt so i don't really get what's the problem.
EDIT: I tried the installation by typing : ```
grub-install /dev/sda --root-directory=/mnt
```

Thanks

Also yes I know my english sucks

---

### Post by Bucky Ball on 2013-12-09
Welcome. English quite fine.

You only need:

```
grub-install /dev/sda
```

You don't need (or want in this case) the other stuff. That's why you're getting the error.

```
Path `/mnt/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
```

It's looking where you told it to and not find anything. Boot from a LiveCD, try my first command and see if it helps. If not, try boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by mintyBrain on 2013-12-09
```

xubuntu@xubuntu:~$ grub-install /dev/sda
mkdir: cannot create directory &#8216;/boot/grub/i386-pc&#8217;: Permission denied
xubuntu@xubuntu:~$ sudo grub-install /dev/sda
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

```

---

### Post by Bucky Ball on 2013-12-09
I think the problem is you need:

sudo grub-install /dev/sda

---

### Post by Bucky Ball on 2013-12-09
> **mintyBrain said:**
> ... what do  you think the problem is here?

The problem is the first grub install you gave. Please read my first post as edited. Your error message tells you it is looking for grub in /mnt, which is where it is not. 

Run Boot Repair if this doesn't work and if that doesn't work run the BootInfoScript using it and post a link to that.

---

### Post by mintyBrain on 2013-12-09
I will try boot-repair.

---

### Post by mintyBrain on 2013-12-09
EDIT: Ok, fixed that.

I now have dual boot!

Thank you guys! :3

---

### Post by Bucky Ball on 2013-12-09
Please share with the community how you fixed it and mark thread as solved by following the instructions in my signature. Thanks and enjoy! ;)

---

### Post by mintyBrain on 2013-12-09
All I did was run boot-repair and that fixed it. Grub now starts up when i start my PC :)

---

