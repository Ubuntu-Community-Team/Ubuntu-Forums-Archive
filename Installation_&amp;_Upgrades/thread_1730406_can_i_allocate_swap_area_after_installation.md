---
title: "can i allocate swap area after installation?"
date: 2011-04-16
forum: Installation &amp; Upgrades
---

### Post by apoorvmunshi on 2011-04-16
can i do this? if yes please tell me the steps...

---

### Post by varunendra on 2011-04-16
Yes you can, and it is very easy. See this: [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)

However, as the given link suggests too- > Keep in mind that when creating a swap file that it may not necessarily  be using contiguous disk blocks (as a swap partition will), and this  could have a negative impact on performance as disk access times may be  longer and the more your system uses swap, the worse it will be...
so creating a swap partition would be a better option IMHO.

To do so, you may use gparted included on the ubuntu live cd.Generally the steps would be:-
[COLOR=Red][B][Important: Since partition manipulation operations have the potential risk of loosing data, it is recommended to back up all your important data before using such tools]
[/B][/COLOR]
[LIST=1]
[*]Boot your computer with the Live CD
[*]Choose "**Try Ubuntu**"
[*]Open **System > Administration > Gparted Partition Editor**
[*]Right-click on any partition which has minimum amount of data on it (to save time consumed in resizing it)
[*]Select **Resize/Move**
[*]Decrease the size of the partition (by dragging the slider, or by defining a smaller size in the "New size (MiB)" field) to get enough empty space for your swap partition.
[*]Again, right click in the newly created empty space and select **New**.
[*]In the File system field, choose "**linux-swap**"
[*]Click on Add, then **apply **the changes  (by clicking on the green tick mark on top) and you're done
[/LIST]
A few things you may need to know:
The size of the swap partition depends upon the amount of RAM in your system. Typically 2 GB is sufficient for upto 2GB RAM. For 4GB or above, you don't need a swap area at all unless you wish to use hibernation feature. For Hibernation support, the swap area must be at least as large as your RAM, or slightly bigger.

Please post back if you find any difficulty regarding this.

---

### Post by apoorvmunshi on 2011-04-16
thanks . i will try this solution. but let me ask u , if i boot through the live CD and make disk changes for swap area allocation then will those changess be applicable to the installed ubuntu system??

---

### Post by Dutch70 on 2011-04-16
> **apoorvmunshi said:**
> thanks . i will try this solution. but let me ask u , if i boot through the live CD and make disk changes for swap area allocation then will those changess be applicable to the installed ubuntu system??

Yes, you will be working on your physical hard disk, not your usb stick.

---

### Post by apoorvmunshi on 2011-04-16
i am very new to ubuntu so could u please briefly explain me the steps ?? 
or u can correct the steps which i am going to take:
1. boot from live CD
2. run the installation application
3. create a swap partition out of a disk
4. what mount point parameters should i give???
5. after partitioning , how can i allocate this swap area to the currentlyy installed ubuntu 10.10 version?/

waiting for u r reply):P

---

### Post by varunendra on 2011-04-16
> **apoorvmunshi said:**
> i am very new to ubuntu..
almost same is my status, don't confuse my beans with "ubuntu experience", they mean nothing :)

> **apoorvmunshi said:**
> or u can correct the steps which i am going to take:
1. boot from live CD
2. run the installation application
3. create a swap partition out of a disk
4. what mount point parameters should i give???
5. after partitioning , how can i allocate this swap area to the currentlyy installed ubuntu 10.10 version?/

waiting for u r reply):P

[LIST=1]
[*]  ok..
[*].. haven't you installed it yet?? Go ahead, and maybe you won't need any guidance from us
[*]ok (well.. the disk would obviously be the fixed hard disk)
[*]swap partition has **no mount point**
[*]swap area, once created, is automatically recognized and picked up for use by any linux OS that you boot into. You don't have to do anything. Think of it as another RAM which the OS itself takes care of.
[/LIST]

---

### Post by apoorvmunshi on 2011-04-16
i have already installed ubuntu 10.10 i will try this.thanks a lot...hope to see u again

---

