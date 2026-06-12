---
title: "Uninstalled Ubuntu, cant boot XP, stuck at GRUB rescue"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by bleachit42 on 2011-02-02
*I was dual-booting X[I]P and Ubuntu 10.10 for a while, but as I  never used Ubuntu it was just taking up space, so I figured I'd get rid  of it. I used a partitioning tool from inside X**P** to remove the Ubuntu **p**artition, forgetting that I used GRUB2 every time I booted to select which OS to load. Now when I start my com**p**uter I get stuck at the "grub rescue>**"** screen. After searching for solutions to this **p**roblem all of them said to either use the Windows X**P** CD to fix the Master Boot Record or reinstall Ubuntu, but I dont have my X**P*[I] CD and there isnt enough room on my hard drive anymore for a Ubuntu install. Is there anything else I can do to fix this?
    
If its of any use, I still have the Ubuntu 10.10 Live CD.

also I'm a[/I][/I]*[I]p*[/I][I][I]parently stuck on italics, so sorry for that :P
[/I][/I]

---

### Post by presence1960 on 2011-02-02
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have a retail XP install disk, then you will need the ubuntu Live CD. Boot the ubuntu Live CD. Choose Try Ubuntu. When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
``` Igonore warnings and proceed. This will install lilo to Live Cd session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```When completed you will have set a generic windows bootloader on the MBR of your disk. Boot without the ubuntu Live CD and you should boot right to windows.

---

### Post by arpanaut on 2011-02-02
^^^ What he said.

Here's a link that should give you the tools and information you need.

[http://ubuntuforums.org/showpost.php?p=10404329&postcount=3](http://ubuntuforums.org/showpost.php?p=10404329&postcount=3)

---

### Post by debd on 2011-02-02
try this method:
insert the Ubuntu live cd> click install ubuntu
now select : "manually partition(advanced user)"  {i dont remember the exact option}
U'll see a window with your disc drives. find out which drive had your ubuntu installation. if you previously installed ubuntu this way ,it will be a lot easier to do.
now just select the partitions where ubuntu was installed, click on the delete button. it will free up the partitions and show "freespace".
after you have done it with all the partitions you may format the free space with "ntsc' as the selected file sysytem.  

hope this will help you get back to the windows boot manager.

---

### Post by bleachit42 on 2011-02-02
> **presence1960 said:**
> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have a retail XP install disk, then you will need the ubuntu Live CD. Boot the ubuntu Live CD. Choose Try Ubuntu. When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
``` Igonore warnings and proceed. This will install lilo to Live Cd session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```When completed you will have set a generic windows bootloader on the MBR of your disk. Boot without the ubuntu Live CD and you should boot right to windows.

I can't get internet on the computer with the problem without loading XP, but I have Ubuntu installed on the laptop I'm on right now, can I download Lilo and put it on the other computer somehow?

---

### Post by presence1960 on 2011-02-02
> **bleachit42 said:**
> I can't get internet on the computer with the problem without loading XP, but I have Ubuntu installed on the laptop I'm on right now, can I download Lilo and put it on the other computer somehow?

If you have internet, when you boot the Live Cd it should detect your internet connection. You can then follow the instructions.

---

### Post by hsingh80 on 2012-01-02
> **presence1960 said:**
> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you don't have a retail XP install disk, then you will need the ubuntu Live CD. Boot the ubuntu Live CD. Choose Try Ubuntu. When the desktop loads open a terminal (Applications > Accessories > Terminal) and run ```
sudo apt-get install lilo
``` Igonore warnings and proceed. This will install lilo to Live Cd session.

Next in terminal run ```
sudo lilo -M /dev/sda mbr
```When completed you will have set a generic windows bootloader on the MBR of your disk. Boot without the ubuntu Live CD and you should boot right to windows.

Thanks a million....this worked for me...I had Win 7 and Ubuntu installed but after deleting the Ubuntu with Gparted I was stuck at grub rescue and grub...Your solution worked perfectly...Appreciate it

---

