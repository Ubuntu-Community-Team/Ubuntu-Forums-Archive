---
title: "partitioning"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by pravit on 2005-05-27
I am trying to set up a WinXP/Ubuntu dual boot system, but I'm not sure how to partition things. What I want to do is have WinXP on one partition, Ubuntu on another, and then a large space where I can access things from both OSes. I have no experience with partioning, however, so I'm probably doing something wrong. I installed Windows first and gave it a 2GB partition. Then I started the Ubuntu install and made partitions as such:
3GB ext3, mount to /, boot flag on
1GB swap
~25GB FAT32, mount to home/

I am not trying to preserve any data; I just want a fresh start, so I'm not going to try shrinking existing partitions or anything. Thanks for any help.

Pravit

---

### Post by camp on 2005-05-27
Hi pravit,

I think everything looks good... except for the /home directory. Don't know for sure how Ubuntu will handle the fact that your users home directories, won't be able to handle linux/unix filesystem security.

I hve my machines setuped as you described. But with one big difference. I have partitioned my disk as follow:

-WindowsXP          -Windows partition(NTFS)
-/                          -Kubuntu partition(ext3)
-/home                 -Kubuntu partition(ext3) mounted on /home. 
-swap                   -swap 
-data                    -FAT32 partition mounted on /mnt/data

I think the first two are self explained.
The third, gives the advantege of reinstalling(or even change the linux flavour) your OS without loose any settings or files.
The fourth I belive you got the hang of to.
The last one. Is a simple FAT32 partition. Make it in your Windows and give it a drive letter(D:\). Then make a directory called "data" under /mnt. After that, edit your /etc/fstab, as root(or sudo) so it will be mounted everytime you boot up your k/ubuntu.

Done! You will now how exactly what I think you wanted. Now you can just put the files and documents you will be able to access from both OS in /mnt/data or from windows D:\.

Have a nice partitioning!
/JC

---

### Post by pravit on 2005-05-27
Thanks for your help! Would like to ask about a couple things, though -
how big did you make your /home? Does it matter? So I should first set up D: in windows as FAT32, then install Ubuntu and give the rest of the space to it? Ah, I'll play around tonight, will probably have to sit through a couple more reinstalls :)

EDIT: It worked! I have myself a dual boot system! Now, to learn Linux... Thanks for your help!

---

### Post by camp on 2005-05-27
Just happy to help! Isn't it what Open Source is all about?

As you said, you already have a working system. But even if it might be a little to late to change the /home partition. Mine is 10GB, but I'm only using 2GB at the moment.

Have a nice weekend and learn linux, it's worth it!   ;-) 
/JC

---

