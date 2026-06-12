---
title: "Can't install 12.04 or 13.10 alongside Windows 7"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by Blakeo on 2014-02-25
Hi guys, I see this has been posted a few times. But I haven't found my solution in either of those threads. 
Basically I cannot get either 12.04.4 or 13.10 to install alongside Windows 7. 
It doesn't display the option instead it gives me this: [IMG]http://i.imgur.com/70UPF5b.png[/IMG]

Sorry about the large image. 

Hopefully someone can help me with this. 
Thank you.

---

### Post by zvacet on 2014-02-25
Do you already have Ubuntu installed?If you do,do you have separate home partition?How many primary partitions do you have on disk?

---

### Post by grahammechanical on 2014-02-25
It seems (and you do not give enough information about your partitioning scheme to be certain) that you have the Master Boot Record partitioning scheme that only allows 4 primary partitions and Windows 7 and the manufacturer have already assigned 4 primary partitions.

The Ubuntu installer is wisely offering the only thing it can offer and that is replace Windows. It needs your permission to do so.

You have to remove/delete one of those primary partitions and possibly also resize another one to create enough unallocated space and then the Installer may offer the Install Alongside option. It will then use the unallocated space to create a fourth special primary partition called an Extended partition and then create inside the Extended partition 2 logical partitions. One will be for Ubuntu. The other will be for Swap.

Regards.

---

### Post by Blakeo on 2014-02-25
> **zvacet said:**
> Do you already have Ubuntu installed?If you do,do you have separate home partition?How many primary partitions do you have on disk?
Now I do, I shrinked the Windows 7 partition by half and installed Ubuntu on that with 4gb of swap space (I have 8gb of ram).

> **grahammechanical said:**
> It seems (and you do not give enough information about your partitioning scheme to be certain) that you have the Master Boot Record partitioning scheme that only allows 4 primary partitions and Windows 7 and the manufacturer have already assigned 4 primary partitions.

The Ubuntu installer is wisely offering the only thing it can offer and that is replace Windows. It needs your permission to do so.

You have to remove/delete one of those primary partitions and possibly also resize another one to create enough unallocated space and then the Installer may offer the Install Alongside option. It will then use the unallocated space to create a fourth special primary partition called an Extended partition and then create inside the Extended partition 2 logical partitions. One will be for Ubuntu. The other will be for Swap.

Regards.

The issue was it wouldn't detect it, at that time I had x1 100mb which was a system partition for windows and then my whole disk was allocated to windows 7.

---

### Post by Mark Phelps on 2014-02-25
So what's your current situation -- it's unclear from your final comments!

Is Ubuntu installed now? Or are you still awaiting instructions on how to do that?

---

### Post by mastablasta on 2014-02-26
it is detected if there are less then 4 primary partition on disk (when formated in MBR mode) and when there is unalocated disk space available. if none of this exists then these are the options offered. sometimes even if the disk setup is made correctly with emtpy disk space the next to option would not appear. in that case one can use something else option (which is basically manual partitioning and setup - i.e. advanced users stuff).

it's been a while since i installed windows, but i believe they have similar options. full disk and partitioning with manual setup. though i believe there is never any alongside option....

---

### Post by Blakeo on 2014-02-26
> **Mark Phelps said:**
> So what's your current situation -- it's unclear from your final comments!

Is Ubuntu installed now? Or are you still awaiting instructions on how to do that?
Basically I had to go with "Something Else" because I couldn't find a solution for my problem. All is working good I think.

> **mastablasta said:**
> it is detected if there are less then 4 primary partition on disk (when formated in MBR mode) and when there is unalocated disk space available. if none of this exists then these are the options offered. sometimes even if the disk setup is made correctly with emtpy disk space the next to option would not appear. in that case one can use something else option (which is basically manual partitioning and setup - i.e. advanced users stuff).

it's been a while since i installed windows, but i believe they have similar options. full disk and partitioning with manual setup. though i believe there is never any alongside option....

> it is detected if there are less then 4 primary partition on disk (when  formated in MBR mode) and when there is unalocated disk space available.
I had these conditions and it still did not detect it, not complaining just feedback.

I had to go with the option "Something Else" and I setup the swap disk to half of my ram so 4GB. If I were to upgrade to 16GB of ram would I have to change the swap to 8GB? I don't understand how this works someone with more experience than me please explain.

Thanks guys.

---

### Post by mastablasta on 2014-02-26
yes i do not know why that option sometimes do not appear.

with 16GB you could leave it at 4GB or remove it altogether. i believe swap is used as space to save some data for hibernation and in case you have low ram disk is used. you probably wont touch it much even with 8GB RAM. but in case you would need it, you created it. if you have the disk space it is no issue. 
i have 2GB ram and gave it 4 GB as well, since i hope i can get more money to upgrade to 8GB. :-) but reading some other threads on this topic. i could have just asign 2 GB for swap anyway.

---

### Post by zvacet on 2014-02-26
I think 4GB of ram is too much if it is not a laptop.Laptop can use it for hibernation/suspend,but for desktop there is no need fo more that 2gb of ram.Feel free to correct me if I´m wrong.

---

