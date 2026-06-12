---
title: "Problems resizing partition during installation"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by serialbox on 2008-08-05
Hi.  I have just recently decided to install ubuntu on my laptop using the dual boot option.  my main OS is windows XP.

Ive seen a few posts about the problem im having but none of the solutions seem to work and I think ive messed up my harddrive.

Ive run into a couple problems.  Ive burned a copy of the latest ISO and booted off the CD.  I chose the option to install and when it gets to the part about resizing the partition this is where it gets messed up.

I have a 160GB harddrive that had 120GB free.  The first time I ran the resizer.. I chose 60gb to resize for ubuntu and then hit the next button.   At this point it froze at the 'resizing' progress bar for about 3 hours and was stuck at 0%.  I assumed something went wrong so I rebooted the laptop, ran chkdsk and everything seemed ok.  I was able to get back into windows without any problems.

I tried burning a a new copy of the CD and tried the installation again.. this time there was less available space for me to resize.. but I dont know where it went because it never completed the last time.. didnt even get past 0% after 3 hours.

So I tried it again.. yes im an idiot... same thing happened.  got stuck for hours at 0%.   Now when I go in there.. there's only 80GB of free disk space left and no clue where the rest is.

Im hoping someone can point me in the right direction.

a)  how to recover all the space that went missing over the failed partition resizing attempts using the ubuntu cd.
b)  information on why the resizing keeps stalling at 0%

thanks

---

### Post by Qchan on 2008-08-05
> **serialbox said:**
> Hi.  I have just recently decided to install ubuntu on my laptop using the dual boot option.  my main OS is windows XP.

Ive seen a few posts about the problem im having but none of the solutions seem to work and I think ive messed up my harddrive.

Ive run into a couple problems.  Ive burned a copy of the latest ISO and booted off the CD.  I chose the option to install and when it gets to the part about resizing the partition this is where it gets messed up.

I have a 160GB harddrive that had 120GB free.  The first time I ran the resizer.. I chose 60gb to resize for ubuntu and then hit the next button.   At this point it froze at the 'resizing' progress bar for about 3 hours and was stuck at 0%.  I assumed something went wrong so I rebooted the laptop, ran chkdsk and everything seemed ok.  I was able to get back into windows without any problems.

I tried burning a a new copy of the CD and tried the installation again.. this time there was less available space for me to resize.. but I dont know where it went because it never completed the last time.. didnt even get past 0% after 3 hours.

So I tried it again.. yes im an idiot... same thing happened.  got stuck for hours at 0%.   Now when I go in there.. there's only 80GB of free disk space left and no clue where the rest is.

Im hoping someone can point me in the right direction.

a)  how to recover all the space that went missing over the failed partition resizing attempts using the ubuntu cd.
b)  information on why the resizing keeps stalling at 0%

thanks

[b][color=darkred]
You need to use Partiton Manager (g-parted). It should be in System --> Administration --> Partition Manager. Use that and fix your partitions. After that, try again.
[/b][/color]

---

### Post by serialbox on 2008-08-05
> **Qchan said:**
> [b][color=darkred]
You need to use Partiton Manager (g-parted). It should be in System --> Administration --> Partition Manager. Use that and fix your partitions. After that, try again.
[/b][/color]

cool thanks.. Will do and this forum may become my new favourite place.

---

### Post by snowpine on 2008-08-05
I would also recommend defragmenting your windows partition before you do anything else.

---

### Post by serialbox on 2008-08-05
> **snowpine said:**
> I would also recommend defragmenting your windows partition before you do anything else.

I did that twice before starting this whole process yesterday.  Do you think I should defrag again after removing the bad partitions?

---

### Post by Qchan on 2008-08-05
> **serialbox said:**
> I did that twice before starting this whole process yesterday.  Do you think I should defrag again after removing the bad partitions?

[b][color=darkred]
Nah. That would be overkill.
[/b][/color]

---

### Post by serialbox on 2008-08-05
well.. I was stumped.  the 60GB of missing space was in the "unallocated" section according to the Disk Management tool in Windows and Gparted on the ubunutu live CD.  

Rather than try to figure out how to merge it back together I just decided to wipe out windows Xp altogether and instead of creating new partitions I just installed ubuntu as my main OS on the one partition.

bye bye windows.. the installation went smoothly and its now running on my laptop perfectly.

maybe when I have time I'll install vmware on ubuntu and put windows on just to have.

thanks for the help

---

