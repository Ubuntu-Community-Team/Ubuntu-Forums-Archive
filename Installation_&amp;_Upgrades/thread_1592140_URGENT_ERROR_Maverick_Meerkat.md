---
title: "URGENT ERROR Maverick Meerkat"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by ProcuratorIncendia on 2010-10-10
PLEASE HELP ME!
I installed maverick meerkat but for some reason there was no install to free space option so I installed onto 32gb of my 170gb windows vista installation. I NEED THAT INSTALLATION. 
Maverick Meerkat cannot detect my windows installation!
Please help me!
EDIT: Read my second post.

---

### Post by ridetheteapot on 2010-10-10
lets see the output of:
sudo fdisk -l /dev/sda

hopes to the best; i don't know off hand what meerkat decides to do when installing like that.

---

### Post by ProcuratorIncendia on 2010-10-10
I checked using a lucid lynx disk and it turns out my vista, and both my other ubuntu installations and the free space have been replaced by it.

WARNING TO ALL PEOPLE HOPING TO UPGRADE: Installation might be faulty.

Yes I am very sure I made it install onto only 32gb of space...it decided to wipe everything...

---

### Post by dino99 on 2010-10-10
make room: [http://partedmagic.com/](http://partedmagic.com/) and prepare your partition to install with the "alternate" iso

---

### Post by ProcuratorIncendia on 2010-10-10
What? Why? My system has ALREADY been replaced...There is something wrong with the installer...Cannonical or whoever controls Ubuntu needs to fix it...

---

### Post by Rubi1200 on 2010-10-10
I suggest you take a look at Testdisk and see if you can recover something:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by JackNocturne on 2010-10-10
You can recover the replaced partition by using a **Live **Cd or USB with **testdisk**. Happened to me once,i used it and it reverted to just before i installed it.

---

### Post by ProcuratorIncendia on 2010-10-10
I don't think it will help. It wiped the entire system. I don't think there is anything to restore.

---

### Post by cariboo on 2010-10-10
Give testdisk a try, it will restore your missing partitions, I had a hard drive go bad a couple of weeks ago, the drive seemed to be blank, Testdisk restored the backup partition table, and allowed me to backup up my data.

---

### Post by ProcuratorIncendia on 2010-10-10
I'll try tomorrow. Thanks for the help. If there is any help you can give me in-case of testDisk not helping that would be great.
Thank-you all. DFTBA!:popcorn:

---

