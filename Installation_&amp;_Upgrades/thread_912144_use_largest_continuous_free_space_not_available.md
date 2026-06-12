---
title: "use largest continuous free space not available"
date: 2008-09-06
forum: Installation &amp; Upgrades
---

### Post by Jamenandrew on 2008-09-06
Greetings,

I currently have vista installed on my laptop. I have two 200 gig drives and used 300g for my vista main partition and created a 70g partition in the process for my planned ubuntu installation. After installing vista I deleted the 70g partition to change it into free space.

Now when I try to install ubuntu and get to the partition page the "use largest continuous free space" is nowhere to be found. I have two guided options to use one of my two hard drives in its entirety but I don't want to do that because it would destroy my vista partition. The only other option is manual and I don't know what to do from there.

Thoughts or suggestions?

---

### Post by Kyosys on 2008-09-06
Maybe try picking manual and doing it there?

---

### Post by duongthaiha on 2008-12-23
same with me. anyone have a clue about what should we do please? Thanks a lot

---

### Post by Titan8990 on 2008-12-23
First off, do you have an empty/free partition on your hard drive to install a operating system on?

---

### Post by hyper_ch on 2008-12-23
2x200 Gb partition and you used a 300gb partition for vista?

---

### Post by duongthaiha on 2008-12-23
> **Titan8990 said:**
> First off, do you have an empty/free partition on your hard drive to install a operating system on?
Thanks a lot for your reply.

I have used the disk manager in vista and shrink option  to create a unlocated space. 

However, when i start the ubuntu installation then it show that space is not useable. Is there anything i need to after shrink the partion?

---

### Post by duongthaiha on 2008-12-23
Also, when i tried to format the unlocated space using vista disk manegerment tool then it show the error message "There is not enough space available on the disk(s) to complete this operation". 

I have look on the net. Some one explain it because I already 4 partion in my laptop (2 of those are EISA from the OEM, 1 is vista partition and 1 where i store my data) so I couldn't have more. There is no option to delete the 2 partition from the OEM in vista so I don't think that I can format it. 

Another question  from me is Is that have anything to do with the installation of Ubuntu? If i use some other software like Gparted or Partition Magic is that possible to solve this?

---

### Post by empty_tank on 2008-12-23
i suggest you use gparted in order to see what is the problem.  Boot either an Ubuntu Live CD or sysrescueCD and run gparted.  

If your laptop has only one physical hard drive with 4 partitions, then you have to merge 2 partitions or delete one partition in order to be allowed to create a new partition with one contigous free space.  Then you can create an extended partition which you can subdivide into several logical partitions which you can use for linux file system like swap and root and others.

---

