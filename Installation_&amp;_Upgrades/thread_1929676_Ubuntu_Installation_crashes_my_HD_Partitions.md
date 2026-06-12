---
title: "Ubuntu Installation crashes my HD Partitions"
date: 2012-02-22
forum: Installation &amp; Upgrades
---

### Post by hawk0815 on 2012-02-22
Hi,
after installation from ubuntu studios was my partition table crashed and ALL DATA LOST.
THANK YOU Ubuntu team ... tahanks, thanks, thanks,

450 GB of DATA LOST .... realy thanks for that great working installation ...

=D>=D>=D>=D>=D>=D>=D>=D>

FU

---

### Post by zvacet on 2012-02-22
Put your Ubuntu live disc in drive and install testdisk package.When you do that follow [this]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step") instructions.I hope it will be helpful to you.

EDIT: What did you choose when you installed Ubuntu?If you want to have ubuntu alongside other OS then when you get to the partitioning stage select **something else**.That will give you option to install ubuntu on free space.

---

### Post by hawk0815 on 2012-02-22
I have 3 HD´s and want to install it on disk 3, alongside with other os´es.
Ubunut creates a PRIMARY partition, i don´t know why. And i say DONT install Grub, but it install grub anyway on the boot sector of disk 3 ... and that crashes my superblock and partion table. i tried testdisk, but it can´t read the disk ... now i try easy recovery .. but i have no hope

---

### Post by trimmer on 2012-02-22
What does Ubuntu have to do with your backup practices? It is and always will be your responsibility to keep backups of your data before working on a mission critical machine.

---

### Post by hawk0815 on 2012-02-22
Nothing, but when I answer NO on the Question 'Install Grub' and Grub will install anywhere and on the wrong partition and destroy the superblock and partition table ... that is not my fault. 2) I had an logical partition for ubuntu and the installation changes this whithout my agreement on his own into  a primary ... that is big bulls... and buggy
No other distribution i ever used makes such changes whithout questing .... and ignores my answers and destroy my data

---

### Post by darkod on 2012-02-22
I have never tried to install studio, but all other versions I have seen do exactly as told if you use the manual partitioning.

If you use any of the guided methods, yes it usually creates one primary for root and one logical for swap if you tell it to use the whole disk.

Also, I have never seen grub install to another partition/mbr than the one you specify.

---

### Post by zvacet on 2012-02-23
Well,I jave to say I had similar problems with particular Ubuntu version (lats one Oneiric).I told during installation **not to format home partition**,but Ubuntu formated it any way.First time I saw something like that.I get a picture how **hawk0815** feel right now,and that is why I suggested testdisk as a solution.If anyone else know how to help OP give him a hand.Don´t lecture him about backups.

---

### Post by trimmer on 2012-02-24
I totally understand your frustration. I am not saying anything to discredit you, but please consider that there is a lot of documentation surrounding the proper installation of Ubuntu/Linux/Grub. I doubt you know all of it and it is possible that you overlooked some obscure instruction. There is an advanced button that you encounter only once in the graphical interface of ubiquity(Ubuntu's installer). In that advanced area(which isn't very advanced if I might add), there are selections of where you would like Grub to be installed. I do not remember one place in the installation process, other than this, where a user is asked "Yes or No" Do you want to install grub?... The selection will allow you to check a box for the physical drive(sdx or hdx replace the x with a,b or c depending on your choice of drives) or it will allow you to check a box for the logical partition(sdx1 or hdx1 the number will correspond with your partition number). The latter of these two would have kept your superblock from being overwritten.

There is always a simpler way and I would ask only that you look for it before making decisions that affect how your computer operates. You may have been able to save all your data early on following the installation by telling fsck where your alternate superblock was located. If the affected OS was Windows, you would not get this opportunity as Windows does not make redundant copies of your superblock. All the more reason to solely use Linux/UNIX.

I assure you, software does not make decisions on its own and I further assure you that Ubiquity did EXACTLY as you told it.

Food for thought.

---

### Post by darkod on 2012-02-24
> **zvacet said:**
> Well,I jave to say I had similar problems with particular Ubuntu version (lats one Oneiric).I told during installation **not to format home partition**,but Ubuntu formated it any way.First time I saw something like that.I get a picture how **hawk0815** feel right now,and that is why I suggested testdisk as a solution.If anyone else know how to help OP give him a hand.Don´t lecture him about backups.

As far as I am aware, this can only happen if you change the filesystem type. For example, if you have your old /home partition as ext3, you need to select ext3 during your new install. If you select ext4 there is no way it can achieve it without formatting it.

In that case it ticks the format box and you have to notice that before you proceed.

I have seen exact thread like this, and after a while the OP conceded he did change the FS type and that's why his /home ended up formatted.

---

### Post by zvacet on 2012-02-24
> As far as I am aware, this can only happen if you change the filesystem type.

I didn´t change filesystem type.It was ext4 and I want it to be ext4.Also I didn´t check box on the left side of format option.Believe me that was not first time I installed ubuntu.But all of this is of little or no help to OP.Some solution to save data will be handy.

---

### Post by zvacet on 2012-02-26
See if [http://www.sucka.net/2010/04/recover-deleted-files-with-ntfsundelete-from-a-ubuntu-livecd/](http://www.sucka.net/2010/04/recover-deleted-files-with-ntfsundelete-from-a-ubuntu-livecd/)
can be of any help to you.
[]("http://www.sucka.net/2010/04/recover-deleted-files-with-ntfsundelete-from-a-ubuntu-livecd/")

---

