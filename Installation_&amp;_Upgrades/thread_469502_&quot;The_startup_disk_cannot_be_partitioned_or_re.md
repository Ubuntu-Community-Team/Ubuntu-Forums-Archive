---
title: "&quot;The startup disk cannot be partitioned or restored...&quot; -- Unique problem"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by roostishaw on 2007-06-09
Hello,

I, like many people, have been receiving the error, "The startup disk cannot be partitioned or restored to a single partition", while trying to launch Boot Camp Assistant on my quest to install Ubuntu. I've been reading about this error for days and have learned that this is usually caused when you have another partition. The strange thing is that I don't have another partition. I've been able to confirm this with Disk Utility (running from both my hard drive and from the install disk) and GParted. Both of the apps confirm the existence of only one partition.

I just repaired the permissions and a "Volume Header" using the Disk Utility on the first install disk. Still no dice.

I'm trying to do this in order to install Ubuntu along with OS X. I did previously have rEFIt installed, but the Ubuntu partition was removed (and I removed rEFIt by hand) in the process of moving to my new, larger hard drive. Could this have messed something up in the MBR (I know it's something else on macs)?

If I hold down Option during boot, I get the option to boot from my mac drive or 'Windows'. When I select windows, I get this error (when I choose the mac disk, it obviously works):

```
GRUB Loading stage1.5


GRUB Loading, please wait...
Error 21
```

I'm sure this will end up being part of the problem/solution...

Anyone know what I can do to fix this and use Boot Camp Assistant to successfully partition my drive in two and install Ubuntu?
Thanks!

---

### Post by roostishaw on 2007-06-14
Update: I just went ahead and did a wipe and reinstall. Everything is crisp and clean.

Now, I still want to install Ubuntu on the same drive. How can I do this while still allowing Boot Camp Assistant to remove Ubuntu and return my drive to a single partition at a later date?

Using the 7.04 instructions from [ [https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook) ], will I be able to later remove Ubuntu using Boot Camp Assistant? If not, how can I install Ubuntu in such a way that I will be able to remove it later on using Boot Camp Assistant?

---

### Post by wrzonance on 2007-10-16
I have this exact same problem. I've been hunting on how to fix it WITHOUT doing a brand new reformat/install etc. I just do NOT want to have to back up all my 'ish to reinstall.

Anyway. I see you gave up. I REFUSE TO GIVE UP! I'll keep google searching (that's how I found this thread.)

---Adam

---

### Post by humhaingaurav on 2008-01-17
Hi Guys, 

 I had this same problem. I actually created a partition using BootCamp and then I used it for time machine. However, when I tried to restore my partition using bootcamp it gave me error it said,"The Startup disk cannot be partitioned or restored..." well with the help of one of my friend I figured how to deal with this problem WITHOUT LOOSING  any data and WITHOUT FORMATTING ANYTHING. 

Just follow these simple steps and you will be done. 

1. Open Disk Utility. 
2. Select the drive which says (55.9 GB Toshiba .... ). **NOTE ** I am not talking about the   
    partition but I am talking about your main disk below which you will see all the partitions of your  
    main disk. SELECT MAIN DISK WHICH SAYS (55.9 GB Toshiba .... ).
3. Then on the right hand side you will see several options such as FIRST AID, ERASE, PARTITION 
     etc. Select PARTITION. 
4. Once You selected the partition you will see the big box with all the partitions of your drive in it. 
    Just select the partition which you want to remove from that box. 
5. Below this box you will see '+' and '-' sign. Just select '-' sign after selecting the disk you want 
    to remove. 
6. After this drag the remaining partition till the end of the box. Make sure on the right side of the 
    box it will say the total size of that partition. 
7. Just hit APPLY after all these. 

And you will be all set. 
Hope this helps.

---

