---
title: "Grub location for 10.10"
date: 2010-11-05
forum: Installation &amp; Upgrades
---

### Post by jis on 2010-11-05
Is there a way to set installation process to install grub to other location than MBR? I did not find option in the desktop image. Maybe the alternate image has it?

---

### Post by Quackers on 2010-11-05
Yes, it's right near the end. IIRC you need to click on the advanced button on the last? screen. But may I ask why you would want to? You will get a brief warning when trying to install grub on a partition.

---

### Post by kansasnoob on 2010-11-05
It's now only available if using the Manual Partitioning option.

[ATTACH]174666[/ATTACH]

---

### Post by Quackers on 2010-11-05
Ah, I haven't used the 10.10 installer yet. I know it is different.

---

### Post by wilee-nilee on 2010-11-05
> **jis said:**
> Is there a way to set installation process to install grub to other location than MBR? I did not find option in the desktop image. Maybe the alternate image has it?

It would be helpful if you told us why you need to put the bootloader in a partition.

---

### Post by kansasnoob on 2010-11-05
> **Quackers said:**
> Yes, it's right near the end. IIRC you need to click on the advanced button on the last? screen.

Not in 10.10 :(

We have a new ubiquity. I've been fighting tooth and nail trying to get some things changed.

Look here:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

That only shows a whole disc install but I'm trying in my spare time to put something together :)

---

### Post by kansasnoob on 2010-11-05
> **Quackers said:**
> Ah, I haven't used the 10.10 installer yet. I know it is different.

That's cool. I know you're a devoted Ubuntu luvr :)

---

### Post by jis on 2010-11-05
Thanks, kansasnoob. I want to put Grub in partition, since I have a master Grub that chainloads various operating systems. That is the only way I know to be able to boot different linuces using their latest kernels.

---

### Post by drs305 on 2010-11-05
You can put G2 in a partition using the "force" option. Grub will complain about using blocklists. Even with the force command, it will complain but will do as you ask.

From a working install:
```
sudo grub-install --force /dev/sdXY
```

From a LiveCd (substitute your Ubuntu partition for XY)
```

sudo mount /dev/sdXY
sudo grub-install --root-directory=/mnt --force /mnt/sdXY
```

Of course, this is with Ubuntu already installed. I haven't used the new installer to know if you can do it from the original install.

---

