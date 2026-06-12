---
title: "Finding menu.lst"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by lanark on 2008-10-23
[Solved]Am new to Linux commands. When I boot to the live cd, I am at ubuntu@ubuntu:~$ in the terminal window. My system in the terminal window is roger@roger-desktop:~$
I wish to boot to the live cd and then change from ubuntu@ubuntu:~$ to roger@roger-desktop:~$ since my menu.lst is located there. What is the command to do this?

---

### Post by WWSmith36 on 2008-10-23
I´m not sure what you are actually trying to do.  The menu.lst file is located in /boot/grub/menu.lst rather than you home folder.

Are you able to normally boot into ubuntu?

---

### Post by lanark on 2008-10-23
> **WWSmith36 said:**
> I´m not sure what you are actually trying to do.  The menu.lst file is located in /boot/grub/menu.lst rather than you home folder.

Are you able to normally boot into ubuntu?
I am right now. But I wish to add an IDE drive. It gets recognized 1st so grub doesn't work. I wish to change the menu.lst to reflect the ide drive as hd0 and the drive with the bootloader as hd1. If I boot to my HD linux I can read my menu.lst by typing the command you mentioned at roger@roger-desktop:~$. But from the live CD, ubuntu@ubuntu:~, I only get a blank page with that command. I need to get to roger@roger-desktop:~ How do I get the menu.lst?

---

### Post by WWSmith36 on 2008-10-23
First I would try configuring you Bios to see if you can swap the drives there as to which is first or second.

If you can´t you can do that, mount your hard drive and edit menu.lst like this.  You will have to substitute the proper partition in the mount command.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
sudo gedit /media/ubuntu/boot/grub/menu.lst
```

If your grub menu does not come up when you boot, you will also have to reinstall grub

```
sudo grub
grub> setup (hd0)
```

Hope this helps

---

