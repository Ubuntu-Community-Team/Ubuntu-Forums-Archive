---
title: "I don't want to corrupt the boot sector"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by trenths on 2005-02-13
Hello, everyone! This is my first time here. Can you help me install Ubuntu 4.1 on a dual boot machine that already has windows xp and Fedora? I understand that you just can't install Ubuntu over an existing Linux product so I will need to delete partitions. I'm afraid that in the process I'll wind up not being able to boot into Windows XP. Is there a safe way to do this?

---

### Post by piedamaro on 2005-02-13
Relax. Just boot the installation. When it comes to partitioning choose what partition you want to use.
Then I suggest to not install the bootloader, but then you have to boot fedora, configure grub to boot ubuntu (just a couple of lines, if you eed them I'll post them), and then finish ubuntu installation.

---

### Post by trenths on 2005-02-13
Yep, I need those lines. How do I get into grup from Fedora? Do I have to use terminal to execute a command? As you might guess by now, I'm not exactly a Linux guru yet. But wait a minute, won't I have to delete an existing Linux partition to install Ubantu? If that's so, how can I boot into Fedora?

---

### Post by piedamaro on 2005-02-13
Yep, no problem though :)
On fedora open a terminal, and type:
su -
gedit /etc/grub.conf

then add these lines (beware to not screw up this file, is vital for booting your oses):
title Ubuntu Warty
        kernel (hd0,3)/vmlinuz root=/dev/hda4 ro 
        initrd (hd0,3)/initrd.img

*BUT* instead of those values (hd0,3 and /dev/hda4), you have to put the values matching your partitions. See the other entry in grub.conf file for an example.

---

### Post by trenths on 2005-02-13
But wait a minute, won't I have to delete an existing Linux partition to install Ubantu? If that's so, how can I boot into Fedora?

---

### Post by einstein05 on 2005-02-13
[QUOTE=trenths]Hello, everyone! This is my first time here. Can you help me install Ubuntu 4.1 on a dual boot machine that already has windows xp and Fedora? I understand that you just can't install Ubuntu over an existing Linux product so I will need to delete partitions. I'm afraid that in the process I'll wind up not being able to boot into Windows XP. Is there a safe way to do this?[/QUOTE]
I installed ubunto over Win 98SE and SuSE9.2 :-) 
You must have a partition prepared, where ubuntu should sit. I used the /boot and /swap from SuSe. It recognized the Linux and Win and wrote the ubunu GRUB over the SuSe GRUB. Very nice.
I intended not to use the ubuntu GRUB and install ubuntu without its own bootloader (GRUB) I was able to select that option during install, but at the end ubuntu managed it to put its own GRUB over the previous bootloader. 
It does not hurt, but you can try it.
You must do a partitioning before you start.

---

### Post by einstein05 on 2005-02-13
[QUOTE=piedamaro]Relax. Just boot the installation. When it comes to partitioning choose what partition you want to use.
Then I suggest to not install the bootloader, but then you have to boot fedora, configure grub to boot ubuntu (just a couple of lines, if you eed them I'll post them), and then finish ubuntu installation.[/QUOTE]
 There is a way to prevent corrupting the MBR.
You need a second hard drive, detach the original drive and install ubuntu on that new drive as master on ID0. Then you hook up your original drive as slave to IDE 0 and configure GRUB to map the original hd.
hard drives are so cheap today.
You need a bootloader in any case, if you want more than OS on your system /and or hd

---

### Post by piedamaro on 2005-02-13
You need a bootloader even if you run just ONE operating system, because a pc without a bootloader is unbootable (from disk).

---

