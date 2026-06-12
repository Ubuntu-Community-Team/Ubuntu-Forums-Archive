---
title: "Ubuntu 8.04 with 2 GB Ram and 0MB SWAP"
date: 2008-06-06
forum: Installation &amp; Upgrades
---

### Post by HishamN on 2008-06-06
Hi,

I installed Ubuntu Hardy with 2 GM ram with no SWAP space!

I have 15GB free space, do I need to add 4GB to SWAP?

Or 2 GB ram is just fine?
If yes I need to add SWAP to my system please tell me how to do it?

Thanks

Regards

---

### Post by avtolle on 2008-06-06
With that much RAM, I'd think a swap partition of 512mb to 1 Gb would work. You'll need to add a swap partition to your hdd, and since I always let the partitioner do this on installation, someone else will need to walk you through the process. It will require booting from the Ubuntu Live CD or the Gparted live CD, shrinking your existing /partition, creating a swap partition of appropriate size with the swap flag set, but again, I let the installer take care of these things.

---

### Post by logos34 on 2008-06-06
here's a good guide:
[https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0](https://help.ubuntu.com/community/SwapFaq#head-75ffcb00cefe143fc380f84d7ea9203f16a596d0)

But use Gparted instead of dd like avtolle suggested

I would make it 1 x your ram, so you can hibernate if need be

---

### Post by HishamN on 2008-06-07
avtolle & logos34

Thanks alot for help, I'll do it today.

Thanks again.

Regards

---

### Post by housam on 2008-06-07
for swap partition , it should be from 1 to 1.5 x RAM ( when RAM is lower than 1 GB ) and 1 x ram ( for RAM over than 1 GB ).
>  Every process running on your computer is allocated a number of blocks of RAM. These blocks are called pages. The set of in-memory pages which will be referenced by the processor in the very near future is called a "working set." Linux tries to predict these memory accesses (assuming that recently used pages will be used again in the near future) and keeps these pages in RAM if possible.

If you have too many processes running on a machine, the kernel will try to free up RAM by writing pages to disk. This is what swap space is for. It effectively increases the amount of memory you have available. However, disk I/O is about a hundred times slower than reading from and writing to RAM. Consider this emergency memory and not extra memory.
If memory becomes so scarce that the kernel pages out from the working set of one process in order to page in for another, the machine is said to be thrashing. Some readers might have inadvertenly experienced this: the hard drive is grinding away like crazy, but the computer is slow to the point of being unusable. Swap space is something you need to have, but it is no substitute for sufficient RAM.
Conventional wisdom creates swap space equal to the amount of RAM. 

How to add a swap partition or swap file ( both are doing the function ): [[COLOR="Red"]_https://help.ubuntu.com/community/SwapFaq_[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by Tomatz on 2008-06-07
> **housam said:**
> for swap partition , it should be from 1 to 1.5 x RAM ( when RAM is lower than 1 GB ) and 1 x ram ( for RAM over than 1 GB ).


How to add a swap partition or swap file ( both are doing the function ): [[COLOR="Red"]_https://help.ubuntu.com/community/SwapFaq_[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

Yeah i would go the page file route. It will be much simpler.

Keep it small. I have 2gb ram and i never use swap but its nice to have it there if need be ;)

---

### Post by housam on 2008-06-07
> **Tomatz said:**
> 
Keep it small. I have 2gb ram and i never use swap but its nice to have it there if need be ;)
it is needed when hibernating or using heavy games and during the downloading.

---

### Post by Unix_Slayer on 2008-06-07
I'm running 8 gigs of ram, but I would never run without a swapfile. My swap file is 12 gigs. I made it that big on purpose. Sometimes the swap will grow, and if it reaches the limit, havoc breaks loose. Anyone else ever use their whole swap file, and the system froze?

```
free -m
```

---

### Post by Tomatz on 2008-06-07
> **housam said:**
> it is needed when hibernating or using heavy games and during the downloading.


Really? Thanks for that :) (sarcasim over)


A swap file of 512mb-1gb with 2 gb of physical ram would be more than sufficent.


12gb??? what the hell are you running to use that much swap unix_slayer?

---

### Post by Unix_Slayer on 2008-06-07
> **Tomatz said:**
> Really? Thanks for that :) (sarcasim over)


A swap file of 512mb-1gb with 2 gb of physical ram would be more than sufficent.


12gb??? what the hell are you running to use that much swap unix_slayer?

Wouldn't you like to know.  I have a mailserver, webserver, and various other apps running 24/7. I'm also working on running a game server. For what game you might ask. I'm not sure at this time, but I need another hobby.

---

### Post by Tomatz on 2008-06-08
> **Unix_Slayer said:**
> Wouldn't you like to know.  I have a mailserver, webserver, and various other apps running 24/7. I'm also working on running a game server. For what game you might ask. I'm not sure at this time, but I need another hobby.

Ahhhh i see ;)

For a momet there i thought you were single handedly trying to work out the mysteries of pi.

:lolflag:

---

### Post by HishamN on 2008-06-08
Thanks guys for helping me, I created a 2 GB partition /dev/sda7 then typed this command:

hisham@hisham-laptop:~$ sudo dd of=/dev/sda7 bs=1M seek=2000 count=0

then I typed:

hisham@hisham-laptop:~$ sudo mkswap /dev/sda7 

then last command:

hisham@hisham-laptop:~$ sudo swapon /dev/sda7 

then gedit fstab and add swap to this file.

now:

hisham@hisham-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2017        908       1108          0         16        421
-/+ buffers/cache:        471       1546
Swap:         2000          0       2000

I think that is, am I correct?

Thanks

Regards

---

### Post by Tomatz on 2008-06-08
> **HishamN said:**
> Thanks guys for helping me, I created a 2 GB partition /dev/sda7 then typed this command:

hisham@hisham-laptop:~$ sudo dd of=/dev/sda7 bs=1M seek=2000 count=0

then I typed:

hisham@hisham-laptop:~$ sudo mkswap /dev/sda7 

then last command:

hisham@hisham-laptop:~$ sudo swapon /dev/sda7 

then gedit fstab and add swap to this file.

now:

hisham@hisham-laptop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2017        908       1108          0         16        421
-/+ buffers/cache:        471       1546
Swap:         2000          0       2000

I think that is, am I correct?

Thanks

Regards

In a terminal type:

```
sudo gedit /etc/fstab
```

Then at the bottom of the file put this:

```
dev/sda7       none            swap    sw              0       0
```

Save


This will make the swap partition mount on boot ;)

---

### Post by Tomatz on 2008-06-08
P.s

gnome-system-monitor is a much simpler way of determining how much swap/free swap you have (but not as accurate).

---

### Post by Tomatz on 2008-06-08
> **Unix_Slayer said:**
> I'm also working on running a game server. For what game you might ask. I'm not sure at this time

Multi theft auto dedicated server???

[http://mtavc.com/deathmatch.html](http://mtavc.com/deathmatch.html)

---

### Post by AnRa on 2008-06-08
You didn't need to create a new partition. You could have created a swap file if it was necessary.

---

### Post by HishamN on 2008-06-08
Thanks guys it seem that I have SWAP now,

[IMG]http://hishamn.googlepages.com/swap.jpg[/IMG]

Tomatz, I did what you say and add swap to fstab.

AnRa because I have free unformatted space I decided to add swap as partition.

Thanks alot

regards

---

### Post by Tomatz on 2008-06-08
> **HishamN said:**
> Thanks guys it seem that I have SWAP now,

[IMG]http://hishamn.googlepages.com/swap.jpg[/IMG]

Tomatz, I did what you say and add swap to fstab.

AnRa because I have free unformatted space I decided to add swap as partition.

Thanks alot

regards

Cool :)

Glad I/we could help

---

### Post by AnRa on 2008-06-08
> **HishamN said:**
> AnRa because I have free unformatted space I decided to add swap as partition.Then I suggest setting the kernel swappiness to 0, so you won't have unnecessary disk IO. :)

---

### Post by HishamN on 2008-06-08
Tomatz thanks again, Your replies give me more experience :).

AnRa I didn't get it! are you mean my SWAP configuration add unnecessary IO to disk?

Thanks

Regards

---

### Post by Rallg on 2008-06-08
I have 2Gb RAM, with a 4Gb swap partition. One day, while fooling with partitions, I inadvertently changed the UUID for swap. Then, Ubuntu did not load swap (reporting 0 swap).

I ran it that way for a week, without problem. Only noticed that swap wasn't loaded while looking around for something else.

Mind you, my applications do not need much memory, and I don't use hibernate. Your results may differ, particularly if you have a laptop that hibernates.

---

### Post by AnRa on 2008-06-08
> **HishamN said:**
> AnRa I didn't get it! are you mean my SWAP configuration add unnecessary IO to disk?Depending on the configuration, the kernel may swap to disk even if it's not necessary, this may or may not affect the performance depending on the way you use your PC. You should google "kernel swappiness" for more information. :)

---

### Post by HishamN on 2008-06-09
Rallg I'm not using hibernates or any heavy SW, just use My NB to brows Internet and some small work like writing on Word processors or editing image.

The heaviest SW I'm using is counter strike 1.6 (game) but before adding SWAP I have no problem with CS.

I add swap space becuase I have free space not used also in case I need to free memory in future.

--

AnRa I'll google it now :).

Thanks alot guys.

Regards

---

