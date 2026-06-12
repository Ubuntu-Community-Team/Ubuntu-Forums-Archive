---
title: "problem at allocate drive space option in ubuntu installation along with windows7"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by sivacharan on 2011-09-25
let me try to give a better explanation for this

in my windows i have 4 partitions they are

(1) c drive(24.32gb,in which used space is 15270mb)---this is where my windows7 is installed
(2) e drive(184.gb,in which used space is 62820mb)---this is where all my data is present
(3) g drive(99.9mb)---this reserved partition for windows7
(4) h drive(25gb)----this is where i want to install ubuntu

_h drive_:to install ubuntu i shrunk the volume of h drive.and now th eh drive has 3.05 gb and the remaining is unallocated space.so now the h drive become

(4) h drive(3.05gb,in which used space is 90mb)

in this unallocated space i want to install ubuntu.is it possible?????
  because if i install ubuntu in c drive i will loose windows7 if i install in e drive i will loose my data.
  So to install ubuntu i started with ubuntu cd.

till the "allocate drive space" everything is ok.in this "allocate drive space " i am very much confused.because ubuntu is showing that there are 4 partitions but those 4 partitions sizes are not same as the partitionsin windows,ther are completely different.the partitions that ubuntu is showing are 

(1) /dev/sda1------this partition size is 1mb
(2) /dev/sda2/-----this is partition size is 104mb.
(3) /dev/sda3/-----this partition size is 26109mb(in which used is 3221mb)
(4) /dev/sda4/-----this partition size is 223842mb(in which i used 67457mb)
    this is why i am confusing ubuntu is showing the different partition sizes
   if now i want install ubuntu which partition do i need to use.
if i choose,becase ubuntu needs alteast 5gb,/dev/sda3,if in that space windows7 is installed becase it is already used 3221mb,as i said i loose it,or if i select /dev/sda4,as it is clearly showing that there is 67457mb used space i.e data i loose all my data.so now which partition do i need to choose for ubuntu installation

             thanks for your reply.........

---

### Post by coffeecat on 2011-09-25
@sivacharan, you already have an active thread on this subject here:

[http://ubuntuforums.org/showthread.php?t=1849735](http://ubuntuforums.org/showthread.php?t=1849735)

Please don't create multiple threads on the same topic. I think this is the fourth you've created.

Thread closed.

---

