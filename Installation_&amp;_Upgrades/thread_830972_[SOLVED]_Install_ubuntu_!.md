---
title: "[SOLVED] Install ubuntu ?!"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by sowhat12345 on 2008-06-16
Hello ! I use windows xp . My harddisk has two parts C which has the windows files and program files and D where I keep my musics . I have my musics burned on dvds . I want to install Ubuntu 8 at the same time I want to use also XP . What should I do ? I started the installation , I did the time and keyboard options but I can't understand what should I do after that . I mean the part of disks . I chose "manually" , and it displays three part the one is hda1 ( C ) , the other hda5 ( D ) and a free space which I had reserved before ( on setup xp I don't remember why :) ) . On this part I couldn't do nothing . Because when I 'm gonna open new part it says me that it has to delete the all other parts . So I couldn't do anythink . Now should I format the harddisk again with windows cd and divide the hdd to three parts :
C(for xp)
D(for my musics which I can open it with ubuntu after I unistall it)
E(for linux)

or

C(for xp)
D(for my musics which I can open it with ubuntu after I unistall it)
A free space (for linux)

or something else ?:confused:

I will be happy for you kind assistance ...

---

### Post by Sef on 2008-06-16
1. You need to dual boot. Read [Psychocat's Installing]("http://www.psychocats.net/ubuntu/installing").

2. **Back up** any data before installing.

3. To help you set up your dual boot: With the Live CD > Applications > Accessories > Terminal

then type in this code:

```
sudo fdisk -l
``` Small L.  Copy and paste the results here.

4. If you do not have free space, then formatting will erase the data on either your C or D drives, depending on which one is reformatted.

---

### Post by sowhat12345 on 2008-06-16
I have both them(C and D) free space to use but I do not want to use the Ubuntu's system files in C . Because I format the part C every month because of winxp :) (which is being braked itself) . So I want the Ubuntu files to be in a new part(which I can open it again , it is not problem to format my pc I use to do) . I can format my pc again it is not problem but in "Psychocat's Installing" does not explain how to install in the part which I have divided before (like D). It just explain the first option (Guided resize and use freed space) which use the part which is used also by xp :(

---

### Post by meindian523 on 2008-06-16
You can do the partitioning manually,use the 3rd partition for Ubuntu which you set aside and don't remember why.

---

### Post by sowhat12345 on 2008-06-16
The free space is just 2 GB :( It is not enough :( And when I'm going to open a new part (for ubuntus files) there, It says me It have to delete (format) also the other parts ...

---

### Post by meindian523 on 2008-06-16
2 GB IS not enough.Could you please go to Applications>>Accessories>>Terminal and post the output of the following command here?```
sudo fdisk -l
```Above it's a small L

---

### Post by sowhat12345 on 2008-06-16
&#304;t is not enough . Please :( Also I said : It is going to format all other part . If it will going to do this ,I did it, it is not problem . I want to know how Ubuntu 8 installing with the last option (manually).

---

### Post by meindian523 on 2008-06-16
I know you want to know how to install using manual partitioning,but I need some information,could you please post the output of the command I gave above.And if I get you correctly,you don't care whether the other partitions are formatted or not,correct?

---

### Post by sowhat12345 on 2008-06-16
I'm sorry I give wrong information . When I select the free space I can open new part . I had not realised it .
I open the terminal and I write sudo fdisk -l 

Disk/dev/sda:80.0GB 8006blabla bytes
255heads,63 sectors/tracks,9733 cyinders
units=cyinders of 16065*512=82252806bytes
disk idetifier:0x22022201
Device    Boot start end    blocks       ID   System
/dev/sda1  *      1  5099  40956blabla   7    hpfs/ntfs
/dev/sda2       5100 9732  3761blabla +  f    w95 ext'd Lda
/dev/sda1       5100 9561  3584blabla +  7    hpfs/ntfs


I don't care if it is going to format . But I want use both operation system . I think I will format the all hdd and I will make the free space bigger than now. But I don't know how to install after I click "new part" after I selected the free space.

---

### Post by websaytdatkom on 2008-06-22
i have the same problem..well, im not sure about it and i cancelled the installation...
i have 4 partitions:
160GB hdd with 1 GB RAM
C: (Windows XP) 40GB
D: (Installed Apps)15GB
E: (My personal Files)80GB
[COLOR="Red"]G: (reserved for linux)20GB[/COLOR]

i want Ubuntu 8.0 to be installed on drive G:. i already formatted this drive using Partition Magic (as NTFS)..

how will i do this???

---

### Post by uidb4056 on 2008-06-22
> **websaytdatkom said:**
> i have the same problem..well, im not sure about it and i cancelled the installation...
i have 4 partitions:
160GB hdd with 1 GB RAM
C: (Windows XP) 40GB
D: (Installed Apps)15GB
E: (My personal Files)80GB
[COLOR=Red]G: (reserved for linux)20GB[/COLOR]

i want Ubuntu 8.0 to be installed on drive G:. i already formatted this drive using Partition Magic (as NTFS)..

how will i do this???

You have only one Hard Disk, the letters mean a partition, the partitions can be primary or extended.

There is a limit that a hard Disk can only have maximum 4 partitions, you have to check if all four partitions are primary, if so what you can do is delete the partition  'G:' and create an extended partition (this kind of partition let you create logical partitions inside to avoid the limit of 4 partitions), when done you can use it for Linux because Linux needs at least two partitions one for root '/' and one for swap.

May be you can found more helpfully info on this link

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by meindian523 on 2008-06-22
and you can't install GNU/Linux on a NTFS partition.Well,theoretically,you probably can,but the response wouldn't be as fast as on native file systems like ext3 or reiserfs.

---

### Post by meindian523 on 2008-06-22
> **sowhat12345 said:**
> I'm sorry I give wrong information . When I select the free space I can open new part . I had not realised it .
I open the terminal and I write sudo fdisk -l 

Disk/dev/sda:80.0GB 8006blabla bytes
255heads,63 sectors/tracks,9733 cyinders
units=cyinders of 16065*512=82252806bytes
disk idetifier:0x22022201
Device    Boot start end    blocks       ID   System
/dev/sda1  *      1  5099  40956blabla   7    hpfs/ntfs
/dev/sda2       5100 9732  3761blabla +  f    w95 ext'd Lda
/dev/sda1       5100 9561  3584blabla +  7    hpfs/ntfs


I don't care if it is going to format . But I want use both operation system . I think I will format the all hdd and I will make the free space bigger than now. But I don't know how to install after I click "new part" after I selected the free space.
Please don't put bla bla.You don't need to type the entire thing,just copy and paste.In this case you have put bla bla at the precise point I need information.

---

### Post by sowhat12345 on 2008-06-23
Thank you all !! I format all my hdd .First I setup windows xp and after ubuntu in the free space which I seperated when I fotmat my hdd...

---

### Post by meindian523 on 2008-06-24
so now you can use both operating systems?Please mark the thread solved.

---

### Post by sowhat12345 on 2008-06-24
Yes I can . Thank you !

---

