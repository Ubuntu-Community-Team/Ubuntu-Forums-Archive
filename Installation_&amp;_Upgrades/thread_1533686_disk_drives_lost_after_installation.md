---
title: "disk drives lost after installation"
date: 2010-07-18
forum: Installation &amp; Upgrades
---

### Post by manishkumar on 2010-07-18
hello evry1
m new to linux. i had installed ububtu 10.04 lts on my laptop, where  windows xp was installed. in windows i had 4 drives(c,d,e,f). since i  installed ubuntu i lost my all drives. it only shows a combined file  system.
please help i hv searched on net but all in vain.
:-(

---

### Post by 23dornot23d on 2010-07-18
What option did you choose when installing linux ..... free space or side by side .....

If you chose use the whole disk ..... it uses the whole disk.

c,d,e,f may only be partitions on one drive ?

How many physical drives do you have too ?

You have posted again ,,,, [POST]("http://ubuntuforums.org/showthread.php?t=1533688") ....

---

### Post by cavalier911 on 2010-07-18
See this thread:
[http://ubuntuforums.org/showthread.php?t=1529824](http://ubuntuforums.org/showthread.php?t=1529824)

---

### Post by manishkumar on 2010-07-18
when installing linux ..... i choose free space
i had 4 physical drives. c(windows was installed in it), d, e, f
but now it shows 1 file system of 250gb(hard disk size).
i dont want to lost my data in other drives.
please help.

---

### Post by manishkumar on 2010-07-18
thanks.
but it seems my prob is different. its not dual boot.
my 4 drives are combined to 1 as it shows in ubuntu.
i thought it will just over rite windows in c drive and all drives will be intact.
when i type sudo fdisk -l it showsthis
0x000203e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29653   238182400   83  Linux
/dev/sda2           29653       30402     6013953    5  Extended
/dev/sda5           29653       30402     6013952   82  Linux swap / Solaris

---

### Post by 23dornot23d on 2010-07-18
What do you see when you type 

**df**

in at the console ?

What you have posted above looks like you have used 3 parts of the first drive,

> 

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29653   238182400   83  Linux
/dev/sda2           29653       30402     6013953    5  Extended
/dev/sda5           29653       30402     6013952   82  Linux swap /  Solaris
sda hard drive for linux


There should be a sda3 and a sda4 somewhere in the extended partition ?

Information for df - [The command df]("http://en.wikipedia.org/wiki/Df_%28Unix%29")
or use (df -h) it gives a more readable output ,,,,,

**df -h**

Also with 4 drives you should see something like this .....

sda sdb sdc sdd

---

