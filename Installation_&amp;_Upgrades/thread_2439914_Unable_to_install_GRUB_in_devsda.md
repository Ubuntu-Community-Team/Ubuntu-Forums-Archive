---
title: "Unable to install GRUB in /dev/sda"
date: 2020-04-03
forum: Installation &amp; Upgrades
---

### Post by hamdhantys on 2020-04-03
I was trying to install Ubuntu Studio 19.10 alongside Windows 10 on my 'hp notebook 15' . In the end the error in the image shows up.

Now I can't even start my windows.

Please help!!!

---

### Post by dmnur on 2020-04-03
Boot the installation media, open a terminal window and type the following command:
```
sudo fdisk -l
```

Then show the output of the command.

---

### Post by Impavidus on 2020-04-03
Bios/legacy mode or UEFI mode? You can't mix them.

If you install [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) in your live session, you can create a boot info summary with a lot of information for us to help you.

---

