---
title: "Partition lister?"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by Rainyday500 on 2012-11-19
I've been happily using Ubuntu on an 8GB Lenovo laptop for a couple of months now. I initially wiped Windows off the 750GB hard drive and installed 12.04, then upgraded to 12.10. Now I'm planning to do a fresh install of 12.10 from scratch so I can encrypt the hard drive.

My question is, how can I look at my current partition information to see how space is actually being used? I stumbled on a program a month or so ago that gave me a nice listing of my current partition scheme and how much space was actually being used in each partition. I'm sure it wasn't gparted, but I can't remember what the program was, though, and I'd like to rejigger my partition scheme a little when I do the fresh install. Can anyone help me out?

---

### Post by offgridguy on 2012-11-19
> **Rainyday500 said:**
> I've been happily using Ubuntu on an 8GB Lenovo laptop for a couple of months now. I initially wiped Windows off the 750GB hard drive and installed 12.04, then upgraded to 12.10. Now I'm planning to do a fresh install of 12.10 from scratch so I can encrypt the hard drive.

My question is, how can I look at my current partition information to see how space is actually being used? I stumbled on a program a month or so ago that gave me a nice listing of my current partition scheme and how much space was actually being used in each partition. I'm sure it wasn't gparted, but I can't remember what the program was, though, and I'd like to rejigger my partition scheme a little when I do the fresh install. Can anyone help me out?
Personally i like parted magic, it contains gparted and more.  avilable in the software
center.

---

### Post by ibjsb4 on 2012-11-19
Was that program Gnome Disk Utility ?

[https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/](https://apps.ubuntu.com/cat/applications/precise/gnome-disk-utility/)

Should already be installed on your system.

---

### Post by UltimateCat on 2012-11-19
Hi:

You should also be able to open the terminal and run:

```
sudo fdisk -1

```The output should provide you with all partitions on the computer your using.
[http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/](http://www.howtogeek.com/106873/how-to-use-fdisk-to-manage-partitions-on-linux/)

Have a good day!

---

### Post by oldfred on 2012-11-19
As part of every backup I run the bootinfoscript which combines a lot of utility scripts together. Boot-Repair adds some additional info but uses bootinfoscript in its BootInfo report. 

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

            Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/](http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.61/)
Page with instructions and link to above new download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Rainyday500 on 2012-11-20
Thanks for the responses, all. None of them were what I remember seeing, but Gparted gave me the info I needed...partition sizes and current disk usage on each. I'm marking the question solved and going to go do a backup... it will be a busy Thanksgiving weekend here!

---

