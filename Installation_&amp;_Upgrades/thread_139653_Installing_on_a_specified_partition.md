---
title: "Installing on a specified partition"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by Rizeup on 2006-03-04
Alright I havent had much luck up to now with installing ubuntu.
I want to dual boot it with windows xp.
Right now windows is installed.
I have my primary partition, some logical partitions and then my linux ext 2 partition. 
For some reason it wont let me select the linux partition to install ubuntu. What am I doing wrong?

---

### Post by 4dz0 on 2006-03-04
When you say it won't let you select the partition what exactly do you mean?

---

### Post by Rizeup on 2006-03-04
I get to the Partition disks section.
I have 4 options.
Resize IDE1 master, partition #5(thats a fat32 partition with some data)
Erase entire disk
Erase entire disk and use LVM
Manually edit partition table

The way I see it, I dont want to install Ubuntu on partition #5 and I dont want to esase my entire disk. So that leaves me with option 4. Manually edit partition table. But then again, I don't want to make any changes to my partitions. Im really not sure how to skip that step without losing any data.

---

### Post by aysiu on 2006-03-04
[QUOTE=Rizeup]
Manually edit partition table[/QUOTE] You want this option.

It will let you select which partition you want to install Ubuntu on.

---

### Post by Xian on 2006-03-04
[QUOTE=Rizeup]So that leaves me with option 4. Manually edit partition table. But then again, I don't want to make any changes to my partitions. Im really not sure how to skip that step without losing any data.[/QUOTE]

You'll need to select that option to at least set your mount points. The only thing that will be written to disk using that method will be the swap file (this is required). Once you set the mount point for at least your root directory the installation will continue. Choose the file system you have already prepared and off you go.

---

### Post by Rizeup on 2006-03-04
ok i think i get it now.
I select the partition I want and edit the mount point to "/" (root) ?
Then it should install on there.
Sorry i'm a linux newb. Trying to slowly make the switch.

---

### Post by Xian on 2006-03-04
[QUOTE=Rizeup]
Sorry i'm a linux newb. Trying to slowly make the switch.[/QUOTE]

Actually, I think the installer could be much improved and the menus provided are not very descriptive of the procedures that are required. In short, it has much more to do with a poor design approach than with your 'newbness'.

---

### Post by Rizeup on 2006-03-04
Its installing :)
Lets hope everything goes well.

Thanks alot for the help.
Very appreciated.

---

### Post by syg00 on 2006-03-04
[QUOTE=Xian]In short, it has much more to do with a poor design approach than with your 'newbness'.[/QUOTE]Agreed - having just installed yesterday.

---

### Post by Xian on 2006-03-04
Well, hopefully the Expresso installer in Dapper will assist in this regard.

---

