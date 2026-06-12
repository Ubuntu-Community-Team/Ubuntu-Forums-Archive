---
title: "Ubuntu 7.10 installation problem on windows system"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by tanu_10 on 2008-01-15
Hi,

while installing ubuntu 7.10 on windows system, I have the problem in creating partitions.
I have 2 primary partitions now. and the free space.
on 1st - windows is installed, 2. recovery data, and now i want to install ubuntu.
so i created 3rd partition as root of 3GB(primary), and swap of 512MB (primary),then i wanted to create 1 more partition as home, but remaining free space becomes as unusable. so i am not able to create /home partition.

Is it ok if i dont create one more partition for /home and do installation with only 2 partitions of root and swap. and remianing free space has become unusable.

please give me any suggestions as how to proceed with the ubuntu installation.

Thanks

---

### Post by ssteinbr on 2008-01-15
Your installation will go fine with only two partitions.  People recommend a separate /home partition because it makes it easier to do reinstalls or try out different distros without losing your personal files.

---

### Post by logos34 on 2008-01-16
You can only have [four primary partitions]("http://www.brunolinux.com/04-The_File_System/Primary_Extended_and_Logical_Partitions.html") on a disk.  You don't really need a separate /home, but they have their advantages.  You can have one if you make an extended partition.

---

### Post by jerrykenny on 2008-01-16
try deleting your linux primary partitions, then create one huge EXTENDED partition, taking all the available space.

Then you can creat as many logical partitions as you like for linux within the exended partition.

---

### Post by tanu_10 on 2008-01-20
hi

yes, my installation is working with only two partitions.
thanks for your suggestion.
does this ubuntu 7.10 installs GCC compiler, GDB debugger also,
i tried to C programs, but it says, there is no stdio.h file , in that case how do i install these.
i dont have the internet, i have just installed ubuntu using live CD.

thanks in advance



> **ssteinbr said:**
> Your installation will go fine with only two partitions.  People recommend a separate /home partition because it makes it easier to do reinstalls or try out different distros without losing your personal files.

---

