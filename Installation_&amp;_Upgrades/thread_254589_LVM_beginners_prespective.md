---
title: "LVM beginners prespective"
date: 2006-09-10
forum: Installation &amp; Upgrades
---

### Post by natarajmb on 2006-09-10
Hi all,
 
 Scenario:
 I have a dell workastation 420 SMP i run a drapper server on it. Recently i found a need to extend my disk space. I taught of using a spare 120GB sata drive connected to my windows pc. I have sucessfully connected this drive over USB internally to drapper. I am able to see this drive by default. 

 Problem: 
 I read this article on Debian Administration   
 [http://www.debian-administration.org/articles/410](http://www.debian-administration.org/articles/410)  
 my quries
 1. Can i use LVM by default with out need of any chage ( What i mean by chage is NOT TO REINSTALL DRAPPER)
 2. If i have to reinstall to get LVM setup, can someone point me to right document which expalins how to enable LVM during install.
 3. Can i add exisiting partions to LVM without loosing data.
    say i have /dev/sda7 as my /home can i add /dev/sda7 to a vloume group with out loosing data.
 
please thow some light on this...
awaiting replys
regards

---

### Post by natarajmb on 2006-09-11
No one here uses LVM? ](*,)

---

### Post by amo-ej1 on 2006-09-11
AFAIK,

When you create the LVM volumes you will need the empty space/partition to create it on. So if you don't want a reinstall you'll end up moving your data between a regular and an lvm partition. As far as I know there is know method of converting existing partitions to LVM since it would impact the structure of the filesystem and such (just remember that a volume group can consist of multiple partitions spanning over multiple disks). I also don't remember the installer offering any direct method to create lvm volumes (but I haven't really searched for it).

If i wanted to switch the data on my system to lvm I'd backup my data to another disk, do the lvm wizardry and migrate the data back. (Eventually, copy the data to another empty partition large enough to contain the data).

---

### Post by keithweddell on 2006-09-11
I don't know if you can transfer your data without reinstalling.  But if you do need to reinstall, you will need to use the "alternate" install cd because the normal live cd does not support an lvm install.

You might also want to look into RAID if you are sharing data across disks.

Keith

---

### Post by natarajmb on 2006-09-11
Thanks for the reply guys,
I finally cleared few of my doubts, This is what
i have understood so far (For benift of others)

By default ubuntu uses LVM during install, you can over-ride this by choosing custom partationing, if you stick to default parationing then you can easly extend or add additional disks witout much hassles. (PLEASE CORRECT ME IF I AM WRONG)

If you have used custom partationing (which in my case is true) then you cant put the partation into LVM unless moving data out of that partataion or stand to lose data. (THIS IS WHAT I INFERED FROM ABOVE REPLYS)

I still want to know what would be the volume groups ubuntu creates by default, i would check this tonight once i go home. and keep you all posted.

Thanks for all the help 
regards

---

