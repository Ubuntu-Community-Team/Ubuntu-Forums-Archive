---
title: "Ubuntu Shows Up Twice in GRUB"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by Unanimated on 2008-06-27
Okay, here's what I've done with Ubuntu that has led me to the problem at hand.

1. I booted up the live CD to see what it was like.
2. I installed Ubuntu as part of the desktop, again to see what it was like at full(ish) speed.
3. I decided that I wanted Ubuntu as my main system, so I did a full installation that took over my D:\ drive.
4. When I was setting up my speakers and Internet connection in the full installation, I thought I was done and checked for updates. U crashed.
5. I rebooted my computer and opened Ubuntu again and signed in.
6. My mouse and a blank desktop was shown. After a long time, my background finally loaded. After a longer time, the white bars at the top and bottom of the screen loaded, but nothing showed up.
7. The next day, I put the CD in again and did another full installation. I chose to use the full D:\ drive for the installation.
8. Now, when I start GRUB, Ubuntu and Ubuntu recovery mode show up twice, but the memtest shows up once. Windows still shows up once.

I guess what I'm really wondering is how I can get rid of the other Ubuntu that I'm not using without getting rid of the one I am. This wouldn't be an issue if an unneeded 10 GB of my hard drive was being taken up, which is a problem. If it involves the terminal, please put the code that I need to input. Thanks!

---

### Post by Pumalite on 2008-06-27
Post:
sudo fdisk -lu

---

### Post by Unanimated on 2008-06-27
Thanks, but what was that supposed to do? It gave me a list and I don't know what to do with it.

---

### Post by Pumalite on 2008-06-27
Copy and paste here.

---

### Post by muteXe on 2008-06-27
paste the output of that command into a post, preferably in a code block.  It helps diagnosing any problems.

---

### Post by Unanimated on 2008-06-27
Disk /dev/sda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders, total 40132503 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc070c070

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    40114304    20057121    c  W95 FAT32 (LBA)

Disk /dev/sdb: 30.7 GB, 30750031872 bytes
255 heads, 63 sectors/track, 3738 cylinders, total 60058656 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x190e190d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63    57496634    28748286   83  Linux
/dev/sdb2        57496635    60050969     1277167+   5  Extended
/dev/sdb5        57496698    60050969     1277136   82  Linux swap / Solaris

Disk /dev/sdc: 2044 MB, 2044198912 bytes
63 heads, 62 sectors/track, 1022 cylinders, total 3992576 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

---

### Post by Pumalite on 2008-06-27
You have Linux installed in sdb1, sdb2 and sdb5 (/swap) There are no other instances of Ubuntu. Give details about your Grub Menu.

---

### Post by Ekeluo on 2008-06-27
You need to edit ur menu.lst(/boot/grub/menu.lst) (as root, i.e. gksu, or sudo from terminal) and remove invalid entries after consulting the above list.

P.s. Doesn't update-grub do this?

---

### Post by Unanimated on 2008-06-27
> **Pumalite said:**
> You have Linux installed in sdb1, sdb2 and sdb5 (/swap) There are no other instances of Ubuntu. Give details about your Grub Menu.
Well, I turn on my computer and it boots from the disk drives. After that, it says GRUB Loading. Then, it bring up a list that looks like this, only it has a bunch of numbers at the end of Ubuntu that I can't remember and so I'm just not going to put them.

Ubuntu
Ubuntu (recovery mode)
Ubuntu
Ubuntu (recovery mode)
Ubuntu memtest+
Other operating systems:
Microsoft Windows XP Professional

EDIT: This is what it says in the menu file:
title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00213b73-c880-4f4e-82dc-493ac67556d3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=00213b73-c880-4f4e-82dc-493ac67556d3 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=00213b73-c880-4f4e-82dc-493ac67556d3 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=00213b73-c880-4f4e-82dc-493ac67556d3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

---

### Post by Unanimated on 2008-06-27
> **Ekeluo said:**
> You need to edit ur menu.lst(/boot/grub/menu.lst) (as root, i.e. gksu, or sudo from terminal) and remove invalid entries after consulting the above list.

P.s. Doesn't update-grub do this?
I just did that, and it looks exactly the same.

---

### Post by bubba_169 on 2008-06-27
Its just you have two kernels installed, nothing to worry about!
Ubuntu always keeps the last kernel incase you have problems with the latest upgrades...

I dont think your first (and faulty) ubuntu install is showing up in grub!

---

### Post by housam on 2008-06-27
looking at your file.lst, you've updated your system from kernel 16 to kernel 19.
you can remove the unwanted kernel from the grub menu by adding the # in front of each line related to that kernel. then save and reboot.
as an example : 
> #title Ubuntu 8.04, kernel 2.6.24-16-generic
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.24-16-generic root=UUID=00213b73-c880-4f4e-82dc-493ac67556d3 ro quiet splash
#initrd /boot/initrd.img-2.6.24-16-generic
#quiet

---

### Post by Unanimated on 2008-06-27
> **bubba_169 said:**
> Its just you have two kernels installed, nothing to worry about!
Ubuntu always keeps the last kernel incase you have problems with the latest upgrades...

I dont think your first (and faulty) ubuntu install is showing up in grub!
Does that mean that I can open the menu file and just remove the last two Ubuntu (not memtest) from the list and it will be fine?

---

### Post by Pumalite on 2008-06-27
You are not removing them. You are just preventing them from showing up in your Grub Menu. Is good to have another kernel to boot from in case of trouble.

---

### Post by Unanimated on 2008-06-27
> **housam said:**
> looking at your file.lst, you've updated your system from kernel 16 to kernel 19.
you can remove the unwanted kernel from the grub menu by adding the # in front of each line related to that kernel. then save and reboot.
as an example :
When I do that, I click save and it says that I do not have permission to save it. Do I need to be on a certain account to be able to save it?

---

### Post by housam on 2008-06-27
> **Unanimated said:**
> When I do that, I click save and it says that I do not have permission to save it.
edit the menu.lst using this code 
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by Pumalite on 2008-06-27
gksudo gedit /boot/grub/menu.lst
Make changes
File>Save
Exit

---

### Post by Unanimated on 2008-06-27
It works just fine now. Thanks everyone!

---

### Post by Ekeluo on 2008-06-28
Well ur problem's solved, wanted to make a suggestion - startupmanager (available in repos) can automatically restrict the number of kernel that show up in grub along with several other nice tweaks it handles.It has a gui so no problem using it, give it a spin. Also you might want t periodically remove i.e. uninstall older kernels if you find the newest one works alright for you. Might save you a few mbs (~80 or so).

---

### Post by Unanimated on 2008-06-28
> **Ekeluo said:**
> Well ur problem's solved, wanted to make a suggestion - startupmanager (available in repos) can automatically restrict the number of kernel that show up in grub along with several other nice tweaks it handles.It has a gui so no problem using it, give it a spin. Also you might want t periodically remove i.e. uninstall older kernels if you find the newest one works alright for you. Might save you a few mbs (~80 or so).
How do I remove the other kernels?

---

