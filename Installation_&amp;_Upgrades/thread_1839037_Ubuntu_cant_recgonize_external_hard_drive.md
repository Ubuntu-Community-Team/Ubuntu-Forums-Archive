---
title: "Ubuntu cant recgonize external hard drive"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by marcioloko on 2011-09-04
Well im newbie to ubuntu,my windows 7 got screwed up,i will format,but before i format the windows 7,i want to save a few things from my hard disk,so i downloaded a the ubuntu to a pen drive,version 11.04 i think,when mount my external hard disk,it doesnt recognize the hard disk.What should i do to ubuntu regocnize? So i can copy my files to the hard disk.


PS: Sorry about my english its not really good,I hope i made myself clear and understandable about the problem.

---

### Post by lmarmisa on 2011-09-04
Welcome to the forums. :D

Please, plug your external hard drive, open a terminal, type these commands and post the results (use the CODE tags - icon **#**):

```

sudo lsusb
sudo lshw -C disk
sudo fdisk -l
mount

```

---

### Post by marcioloko on 2011-09-05
> **lmarmisa said:**
> Welcome to the forums. :D

Please, plug your external hard drive, open a terminal, type these commands and post the results (use the CODE tags - icon **#**):

```

sudo lsusb
sudo lshw -C disk
sudo fdisk -l
mount

```


I think i explained wrong,I meant my external hard drive,not my hard disk.My hard disk i can acess the files,but  the external hard disc it shows a ERROR,I will post when i will get home.

Those codes it doesnt delete the files from both hard drives? Because i cant delete nothing from the external hard drive and from the hard disk from my laptop,its really important files.

---

### Post by lmarmisa on 2011-09-05
Those commands will provide information about both internal and external hard drives. 

Anyway, post the error that your system shows. I hope that this information will be useful.

Best regards,

Luis

---

