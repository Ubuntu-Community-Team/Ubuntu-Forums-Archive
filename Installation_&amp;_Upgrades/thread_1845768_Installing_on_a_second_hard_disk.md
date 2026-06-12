---
title: "Installing on a second hard disk"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by Roger49 on 2011-09-17
Hi,
I've been trying out Ubuntu as a possible replacement for Windows. I've been running it from a usb hard disk. I've taken the decision to install on a second, internal SATA disk.
Currently, my bootable Windows disk is shown in GRUB as sdb, and my old unbootable Windows95 disk is shown as sda.
I want to ensure that I boot to GRUB and have the choice of Ubuntu or Windows.
Should I move my Windows disk to the "sda" position and install the new disk in the "sdb" position, using the relevant connectors?
My old Windows 95 disk will be taken out.
I would be grateful for any comments. Just let me know if you need any other info.
Regards,
Roger49

---

### Post by oldfred on 2011-09-17
XP has drive & partition info in the boot.ini. If you change the drive number you will have to edit boot.ini. Win7 and Vista converted to a BCD that does not seem to care, but may require some update, more like Ubuntu in using UUIDs to keep track of partitions.

On Ubuntu drive you want to use manual install so on the partitioning page you also get the option on where to install the grub2 boot loader. You want to install to the same drive. All the auto install options will install grub2's boot loader to sda.

Installing Ubuntu in Hard Disk Two (or more) Maverick 10.10
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

---

### Post by Roger49 on 2011-09-18
Hi,
Thanks for the reply and the links.
As I seem to understand it then, the best bet would be for me to install the new hard disk using the connector previously used by my unbootable W95 HD. Put Ubuntu, and grub onto it, and change the boot preference in BIOS to the new HD?
I should be able to do a manual install OK, I would like to get a separate /home partition anyway.
Regards,
Roger49

---

### Post by YesWeCan on 2011-09-18
A sensible precaution is to disconnect your Windows OS drive while installing Ubuntu. Afterwards, reconnect it. Then boot Ubuntu and in a terminal run
[COLOR="DarkSlateBlue"]sudo update-grub[/COLOR]
to add Windows to your Grub boot menu.

---

### Post by Roger49 on 2012-03-05
Thanks for your assistance.
Now running 10.04 LTS on separate hard disk.
Regards,
Roger.

---

### Post by oldfred on 2012-03-05
Glad you got it working.

That is one of the longer installs I have seen. It usually takes me about an hour.:grin:

---

