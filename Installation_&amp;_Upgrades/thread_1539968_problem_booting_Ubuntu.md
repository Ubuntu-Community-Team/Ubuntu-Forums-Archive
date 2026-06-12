---
title: "problem booting Ubuntu"
date: 2010-07-27
forum: Installation &amp; Upgrades
---

### Post by Panos_Papajohn on 2010-07-27
[SIZE=2][FONT=Comic Sans MS]Hello

I'm new to the Ubuntu family (just installed Lucid Lynx) and I'm having a problem with the installation. I've burned the ISO file to a DVD and follow the instructions for the installation. When I had to create a partition for the Linux I created one to my external HD. Now every time I restart my PC it can't boot neither Windows nor Ubuntu and I'm staring at a black screen. When I put the DVD the PC boots and I can use Ubuntu. But on the desktop there is a file *Install Ubuntu 10.04.* If I open the file I following the same procedure as in the first install. I thought that the bootloader had a problem so I used the terminal app to inform the bootloader about the two OS (Windows and Ubuntu) but when I used the *sudo grub* command I get the message : sudo: grub: command not found
. As I said I'm new to Ubuntu so I don't have a clue what to do so if anyone can help me I would appreciate it.;)
[/FONT][/SIZE]

---

### Post by VH-BIL on 2010-07-27
find out what hard drive your system is booting then I think the solution is to run the command 
grub-install <device to install the master boot record>

---

### Post by oldfred on 2010-07-28
With external drives you want to use the advanced button on the last partition screen to install grub to the external. Then set BIOS to boot external. If external is not there, then windows will still boot.

You need to make sure you have windows boot loader in sda and grub2 installed in sdb (or whatever drive the external is).

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you want specific instructions, plug in the external and from liveCD run this script which documents how your system is set up:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

