---
title: "installing Ubuntu on a seperate HDD"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by Jonker on 2011-03-19
Hello,

I would like to install Ubuntu on the second HDD of a computer. On the primary HDD there is Windows XP. Is this possible?

---

### Post by howefield on 2011-03-19
Absolutely,

My preference would be to use the Live CD to create the partitions where you want them, then use Manual Partitioning option during the install to mount them. At that stage you can tell the installer where you want to install Grub to, depending on whether you want grub to overwrite your windows bootloader or not.

---

### Post by Dutch70 on 2011-03-19
Unless you really know what you're doing. I recommend unplugging your hdd with windows on it, so you can't mess it up. After installing Ubuntu to the 2nd hdd. Log-in to make sure everything is working. Then shut down, plug in your 1st hdd, boot back into Ubuntu, probably by hitting your "esc" key to go into the bootloader. Choose the hdd with Ubuntu on it. When you get logged-in to Ubuntu, run the following command in terminal.

```
sudo update-grub
```

You should be able to see it as it picks up your windows hdd. The next time you reboot, you'll be able to choose Ubuntu or windows from a Grub menu.

---

### Post by Jonker on 2011-03-19
ok, thanks!!!

---

