---
title: "Installing Windows 7 After Ubuntu 10.4"
date: 2010-07-10
forum: Installation &amp; Upgrades
---

### Post by alan2796 on 2010-07-10
I am being forced to re-install Windows 7 on my new laptop just because I need to run iTunes and Nokia Ovi suite, Wish I didnt but here goes.

I completely removed windows and all it's backup Partition's it needed and did a complete ubuntu install, so i have a 320gb hard drive with 3 partition's  

ext4,extended,swap 

am I right in saying if I boot into a live cd and partition the ext4 partition in half leaving me a unallocated partition and then extended and swap partition is that ok to have my windows in the middle of my linux partitions if that makes sense ?

ext4,unallocated,extended,swap

and also after I install windows i understand ill loose grub, but again if i boot into a live CD and reinstall it, all should be well again ?

---

### Post by skarme on 2010-07-10
I'm not sure if this would be the best way to go about this. It could lead to issues later on. There is no harm re-installing Ubuntu and getting a clean and systematic arrangement. Best method would be to format your drive, create at least two partitions, if not more. Install Windows 7 and then install Ubuntu 10.04. With Ubuntu installed this way, the Swap space can be auto created with no issues.

---

### Post by alan2796 on 2010-07-10
hmm, not really willing remove my Linux install I just got it the way I want it.

it seems  ridiculous to install an entire operating system for 2 applications !

---

### Post by bigseb on 2010-07-10
> **alan2796 said:**
> hmm, not really willing remove my Linux install I just got it the way I want it.

it seems  ridiculous to install an entire operating system for 2 applications !
You don't need to. Here is my setup:
[ATTACH]163014[/ATTACH]
It works just fine. Never had any problems.

As regards to grub, yes Windows 7 will kill it. But its a real doddle to fix with your Live CD. So install your Windows 7, then:


1) You need to sure which partition is your Linux partition:
[FONT=monospace]
[/FONT]sudo fdisk -l       (that's a lower case 'L' btw)

2) Next you need to mount you Linux partition:

sudo mount /dev/sdXY /mnt     (replace 'XY' with the right values shown in step 1)

3) Reinstall grub:
[FONT=monospace]
[/FONT]sudo grub-install --root-directory=/mnt/ /dev/sdX      (again, replace 'X' with the right value form step 1. Note: there is no 'Y' value)

4) Reboot    (should boot directly into Linux)

5) Update Grub:

sudo update-grub    (this will add Windows 7 to your boot options)

Easy peasy japanesey!

---

### Post by alan2796 on 2010-07-10
i think ill give that a go, and well if it doesn't work out ill do a fresh install of Windows first then Ubuntu.

id prefer to only have ubuntu mind you !

---

### Post by bigseb on 2010-07-10
> **alan2796 said:**
> id prefer to only have ubuntu mind you !
Why not just run Windows 7 in Virtualbox? After all its only two programs you need it for...

---

### Post by alan2796 on 2010-07-10
how would you go about doing that then ?
i have looked into it a bit but not sure what im doing really

--UPDATE--

Thats me back on Ubuntu after Installing windows 7 worked as expected, but guess what, almighty windows cant recognize my wireless card.

---

### Post by bigseb on 2010-07-12
> **alan2796 said:**
>  almighty windows cant recognize my wireless card.
Missing drivers methinks

---

### Post by Bluesan on 2010-07-12
[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Dual-Booting_Windows_and_Ubuntu)

---

