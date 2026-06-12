---
title: "Help fixing GRUB"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by LieToPurify3 on 2008-02-22
On my laptop, i had ubuntu installed alongside DSL in a dual boot configuration.  DSL started giving me prpoblems, so now i installed Slackware in its place, but in my GRUB, it still lists Ubuntu and DSL as my OS's.  How can i change it so that it will boot my Slackware partion now?  Its not like it just says DSL, but if i choose it, it boots Slackware.  If i choose DSL, i just get errors.  I had to resize my partitions in order to install Slackware; i'm not sure if that affects anything.  Is there any way i can either fix this, or remove grub and reinstall it? or even install lilo instead? thanks

---

### Post by banewman on 2008-02-22
You need to open a terminal and type in the command -
sudo update-grub
and grub will re-write the entries in the /boot/grub/menu.lst file
:)

---

### Post by LieToPurify3 on 2008-02-22
i tried doing that and my grub menu still lists ubuntu, ubuntu recovery mode, ubuntu memtest, and then in "Other" OS's, it has 4 versions of DSL at different resolutions  (the same as it was before i ran the command)

---

### Post by maybeway36 on 2008-02-22
Look in your slackware partition and copy the stanzas in its /boot/grub/menu.lst to the Ubuntu one.

---

### Post by Pumalite on 2008-02-22
You can mount all your partitions and edit menu.lst according to your desires after backing up the file. Copy and paste the relevant portions from the other menu.lst¡s

---

### Post by LieToPurify3 on 2008-02-22
maybeway, in my slackware partition, there is no /grub folder in the /boot directory.  
Pumalite, i found my menu.lst file in /boot/grub/ in my Ubuntu partition, but i can't find any menu.lst file in the slackware partition.  I never had an option to do anything with grub while installing slackware, so maybe it doesnt' even recognize that i have grub installed?  I'm pretty new to linux, so im trying to jump in and learn as much as i can.

---

### Post by confused57 on 2008-02-22
I no longer have Slackware installed, but here's the entry I used:
```
title           Slackware12.0 on /dev/sda6 vmlinuz
root            (hd1,5)
kernel          /boot/vmlinuz root=/dev/sda6 ro
boot
```

You'll have to modify it to your current Slackware partition.

---

### Post by LieToPurify3 on 2008-02-22
I know i have my Slackware root partition set as hda1, so what would I put?

And would I just delete all the lines with the DSL stuff?

---

### Post by Pumalite on 2008-02-22
For hda1, (hd0,0)
If you don't have DSL any more; erase the lines

---

### Post by LieToPurify3 on 2008-02-22
actually, its on hda4. hda1 is my swap.  but can you tell me how i'd know (or where i can find out) how hda4 would translate into the syntax that grub understands?

---

### Post by confused57 on 2008-02-22
> **LieToPurify3 said:**
> actually, its on hda4. hda1 is my swap.  but can you tell me how i'd know (or where i can find out) how hda4 would translate into the syntax that grub understands?

Try this:
```
title           Slackware12.0 on /dev/hda4
root            (hd0,3)
kernel          /boot/vmlinuz root=/dev/hda4 ro
boot
```

---

### Post by LieToPurify3 on 2008-02-22
thanks! that worked and it started to boot, but then it had another unrelated problem that wouldnt let it boot. i must have had a problem during install.  so in (hda0,3), the first number is the drive that its on (0=a), and then instead of the partitions being listed 1-4 or whatever, it starts at 0?  so 0 would be hda1, 1 would be hda2?

---

### Post by confused57 on 2008-02-22
> **LieToPurify3 said:**
> thanks! that worked and it started to boot, but then it had another unrelated problem that wouldnt let it boot. i must have had a problem during install.  so in (hda0,3), the first number is the drive that its on (0=a), and then instead of the partitions being listed 1-4 or whatever, it starts at 0?  so 0 would be hda1, 1 would be hda2?
Post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

and your boot entries in menu.lst:
```
gedit /boot/grub/menu.lst
```

Guide to grub's numbering system:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

---

### Post by confused57 on 2008-02-23
I had to investigate my computer to find out where Slackware's vmlinuz(a symlink to one of the huge kernels, don't remember which one) was located:
```
sudo grub
find /vmlinuz
```
If I remember correctly Slackware didn't show vmlinuz being in the / filesystem, so I did:
```
root (hd1,5)/
```
Pressing the tab key showed the directories in the Slackware / system...I noticed there was a boot directory, so I did:
```
root (hd1,5)/boot
```
Pressed "Tab", which showed the vmlinuz symlink, and the other kernels located in the boot directory.  When finished, enter quit at the grub prompt(grub>).

This enabled me to direct grub where to find the kernel to boot Slackware:
```
kernel    /boot/vmlinuz root=/dev/sda6 ro
```

I followed this guide to do the above:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

