---
title: "Cant access Vista on my Machine"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by Munyua on 2010-04-29
I cannt access my vista after installing Ubuntu 8.04 on a Toshiba with 250gb I am unable to access the windows partition since its only the linux partition being displayed. Please help me out

---

### Post by Gbeattie on 2010-04-29
the answer to your question will depend on whether you hace installed ubuntu beside vista or deleted vista and formatted your hard drive to install only ubuntu

---

### Post by coffeecat on 2010-04-29
> **Munyua said:**
> I am unable to access the windows partition since its only the linux partition being displayed.

What do you mean by that? Do you mean that the grub menu (the boot menu that gets displayed soon after you switch on the machine) only gives you Ubuntu as a choice? Or do you mean that you've looked at the partition layout and there are only Linux partitions?

Boot into Ubuntu and open a terminal (Applications > Accessories). Post the output of this command:

```
sudo fdisk -l
```When you post the output, please highlight the output text in the message box and click on the # icon in the toolbar in order to enclose it in code tags. That will tell us your partition layout and we can take it from there.

---

### Post by P4man on 2010-04-29
If I remember correctly, ubuntu 8.04 did not mount ntfs (windows) partitions automatically. It can do it though, it just involves a bit of work. It would help if you answered the above questions (wubi install or not and output of fdisk -l) but I also have to ask, is there a reason you installed 8.04? If you want a LTS version, 10.04 is being released later today.

---

### Post by thebigob on 2010-04-29
Can you take a screen shot when you click 

System -> Administration -> Disk Utility

Usually you will see a disk with two or more partitions

EXT* partitions are linux and ntfs or fat are usually windows.

If you see a partition that is the size of your windows install you can mount this using the disk utility tool by clicking the icon in the top left

Once mounted you can access this from your places menu

Attached a screen shot to help

---

### Post by P4man on 2010-04-29
thebigob, he is using ubuntu 8.04. Its has no such disk utility.

---

### Post by thebigob on 2010-04-29
> **P4man said:**
> thebigob, he is using ubuntu 8.04. Its has no such disk utility.

Ah my bad :)

The disk should really be showing in the places menu if it is correctly partitioned.

In this case to get the same information the sudo fdisk -l command is correct

---

