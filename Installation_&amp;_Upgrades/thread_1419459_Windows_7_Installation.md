---
title: "Windows 7 Installation"
date: 2010-03-01
forum: Installation &amp; Upgrades
---

### Post by bbourdet on 2010-03-01
Hello All -

I need to install windows 7 on my computer and I already have ubuntu installed and I am more than happy with it. Is there a way that I can copy what I have already configured in Ubuntu so that I can just wipe my drive, install windows and then put ubuntu back on the exact way it was before?

Thanks!

Tarken

---

### Post by presence1960 on 2010-03-01
You don't need to do all that extra work. create a partition or unallocated space to install windows 7 onto. After windows is installed then reinstall GRUB.

The only thing that happens when you install windows after linux is that windows overwrites GRUB on the MBR with windows bootloader. All you need to do is restore GRUB after windows is installed.

But if you insist on doing it the hard way you can use [clonezilla]("http://clonezilla.org/") to make an image of your ubuntu and then restore using that image.

---

### Post by zeroseven0183 on 2010-03-01
Yes, you can. Almost all of your data and configuration for that user is in the Home folder (that is, /home/<username>). You can back it up somewhere else while running LiveCD.

For more details, follow:
[Ubuntu Community Documentation: Dual Boot Ubuntu and Windows]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")
[Lifehacker: Dual-Boot Windows 7 and Ubuntu in Perfect Harmony]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")

You also have the option to install Windows while Ubuntu is there. No need to wipe the hard drive all over again.

---

### Post by bbourdet on 2010-03-01
> **presence1960 said:**
> You don't need to do all that extra work. create a partition or unallocated space to install windows 7 onto. After windows is installed then reinstall GRUB.

The only thing that happens when you install windows after linux is that windows overwrites GRUB on the MBR with windows bootloader. All you need to do is restore GRUB after windows is installed.

But if you insist on doing it the hard way you can use [clonezilla]("http://clonezilla.org/") to make an image of your ubuntu and then restore using that image.

How do I do that in Ubuntu? I have used the whole disk as only one partition. I am only using 52% of the drive though...

Tarken

---

### Post by presence1960 on 2010-03-01
> **bbourdet said:**
> How do I do that in Ubuntu? I have used the whole disk as only one partition. I am only using 52% of the drive though...

Tarken

Boot the Live CD and choose "try ubuntu without any changes." When the desktop loads open a terminal and run ```
gksu gparted
```

When gparted loads right click your single partition and choose Resize/Move. Use the slider to shrink the partition. When you have the amount of space you want for windows click Resize/Move. Then click the green check mark on the tool bar to apply. Let it finish it may take some time. When complete you will have unallocated space next to your partition. You should then be able to install windows to the unallocated space so boot the windows 7 DVD and proceed.

You have to use the ubuntu live CD or gparted Live CD because you can not do it from Ubuntu because the partition will be mounted- you can't resize a mounted partition.

---

