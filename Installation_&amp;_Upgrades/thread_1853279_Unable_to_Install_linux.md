---
title: "Unable to Install linux"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by Kushagra.19 on 2011-10-02
I have tried many times to install linux but all the time i ge disappointed ..

Plese help me out

i m running windows 7 and i have created a partition of 17 gb
but when i boot with the linux cd and at the last step when i choose that 17 gb partition it says "Insufficient memory to install" .

It is showing the same message when i created the 50 gb partition ..

Please help me out ..

---

### Post by 2F4U on 2011-10-02
Did you create this one partition as a primary or as an extended partition and how many partitions are on your system. You can only have four primary partitions.

---

### Post by Kushagra.19 on 2011-10-02
> **2F4U said:**
> Did you create this one partition as a primary or as an extended partition and how many partitions are on your system. You can only have four primary partitions.

Yeah it the primary partition only.

for more clearance i m enclosing image of my drives partition status ..

---

### Post by Quackers on 2011-10-02
As 2F4U has said, you are only allowed 4 primary partitions on a mbr partitioned disc. In trying to create a 5th partition you have now changed your partitions from basic partitions to dynamic discs.
This means that the Ubuntu installer cannot now see your partitions at all. Ubuntu will not install to that drive now.

You will have to re-install Windows or try to convert those partitions back to basic. There are a couple of threads on how to do that, though a lot of people have just re-installed Windows. Here is one thread on that subject - see post #5

[http://ubuntuforums.org/showthread.php?t=1669910](http://ubuntuforums.org/showthread.php?t=1669910)

If you get your partitions back to basic, or re-install Windows you MUST delete a primary partition BEFORE creating a new EXTENDED partition for Ubuntu (or allow the Ubuntu installer to do that). 
You may also need to defragment Windows and shrink the C: drive (with Windows Disk Management console) to give the necessary free space.

One more point.
If you appear on the forum as not signed in people think you have left, so will be less likely to offer help.

---

### Post by Iowan on 2011-10-04
Closed.
Duplicate thread [here]("http://ubuntuforums.org/showthread.php?t=1853302").

---

