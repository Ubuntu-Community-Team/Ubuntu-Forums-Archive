---
title: "deleting a linux partition"
date: 2008-03-24
forum: Installation &amp; Upgrades
---

### Post by makalove on 2008-03-24
okay, i'm a linux noob, so be gentle :)

i installed ubuntu (7.10 gutsy) on my laptop a few weeks ago. all has been going swimmingly. then a couple of days ago it broke - wouldn't complete a boot. i used the live cd to get online and search for answers, and i ended up reinstalling, allowing the installer to partition my previous install and leave it alone. (it asked me if i wanted to import users but it didn't seem to import anything!)

now i'd like to get rid of that partition altogether. what's the best way to do this?

---

### Post by forestpixie on 2008-03-24
With gparted on the livecd - make sure you delete the right partition - if you're not sure you're menu.lst will tell you which partition you're booting with, use the fdisk command to get partition names.

cat /boot/grub/menu.lst
sudo fdisk -l

---

### Post by anuban on 2008-03-26
> **forestpixie said:**
> With gparted on the livecd - make sure you delete the right partition - if you're not sure you're menu.lst will tell you which partition you're booting with, use the fdisk command to get partition names.

cat /boot/grub/menu.lst
sudo fdisk -l

I have been using Ubuntu extensively for the last 6 months.  And I am very happy to say that I am really a great fan of Ubuntu.:guitar:
Now I want to start over again so as to do a clean install of Hardy.
How do I do that?  I did a upgrade to Beta but I want to do a clean install.  I know I will get Hardy automatically as it is released.
The only thing which I don't get is how do I create/delete/re-create my dual booted with Vista laptop.
When I try to install Hardy from LiveCD, I am held up at the partition manager.
At present I have following partitions:
[LIST=1]
[*]EISA Configuration - 55MB
[*]OS (Vista) - 80GB
[*]Recovery (Vista) - 10GB
[*]Ubuntu (ext3) - 13 GB
[*]Swap - 600MB
[*]Media Direct - 2GB[/LIST]It is a Dell Inspiron 1505 Laptop with 2 GB RAM and 120GB HDD preinstalled with Vista Home Premium.

When I try to format Ubuntu (ext3) partition keeping swap the same and without touching anything else, Partition manager gives me an error message talking about some Clusters and all which Windows won't like and should be something else, I am getting something else. :confused:
Is there a way to completely get rid of Ubuntu so that I can START OVER.

Any help will be appreciated.:(

---

### Post by solaceinsilence9 on 2008-03-26
load gparted from the LIVECD it will show you all your partitions. then just unmount the linux partition and delete it. but BE CAREFUL doing this. I just deleted my Ubuntu partition and reinstalled it and moved and resized my partitions with gparted. After that I cant boot Windows. It just drops me into the GRUB menu and when I select Windows it restarts BIOS and drops into GRUB again. Havent figured it out yet. But just a warning. Good luck

---

