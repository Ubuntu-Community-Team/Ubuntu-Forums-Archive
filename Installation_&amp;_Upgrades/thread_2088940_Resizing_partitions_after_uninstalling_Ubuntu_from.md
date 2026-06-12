---
title: "Resizing partitions after uninstalling Ubuntu from Win dual boot"
date: 2012-11-27
forum: Installation &amp; Upgrades
---

### Post by jmvizanko on 2012-11-27
I decided to uninstall Ubuntu from my dual boot PC, as I was never using it, and I gave it half of my hard drive when I installed it for some dumb reason.  So I repaired BCD with EasyBCD, and my startup goes straight into Windows.  Yay.

Now I am trying to resize my Windows partition.  However, when I fire up EaseUS Partition Master, my Windows C partition has a D parition in between it and what was my Ubuntu partition.  This drive is allocated a whopping 209 Gb, but all it has in it is a SamsungRecovery folder and 3 other crazily named folders that all only total 14Gb.  As far as I can tell, I cannot resize the C partition into the the unallocated Ubuntu partition, as they are separated by the D partition.

What are my options?  Can I resize "around" the D partition somehow?  Can I merge the two partitions?  Can I backup D, blow it away, go about merging, and create it again (and if I do something like that, will I be able to use that recovery with the magic buttons at startup like I normally would be able to)?  I can always just turn the Ubuntu space into an NTFS partition and have my hard drive "split in half," but I have to imagine there's some way to accomplish what I'm trying to do.  Thanks for any help.

(If only I hadn't ran with Wubi for a while......)

---

### Post by jmvizanko on 2012-11-27
Nevermind, just had to keep trying different software.  MiniTool Partition did the trick.

---

### Post by StinkySQL on 2012-11-27
I've not had much luck with repartitioning Windows. Lot's of stuff hidden under the hood. I am told by my peers that the best bet is "partition magic" but I think you have to pay for it , and you could lose both partitions.

Until I got Ubuntu, I never ever considered merging partitions. If you want to deallocate all non-c: partitions, then reboot, then make a new D: you might be in luck.

Also, in a Windows world the drive letters are not significant. You should be able to set them to whatever letter you like. 

Finally, take a close look at that d: drive and make sure it is not actually reporting megabytes. I've made that mistake. Most windows recovery disks I've seen are around the 8 MB size.

Playing with partitions in Windows is fraught with danger. Be prepared to lose it all if you do - worse case anyway ;). 

SS

---

### Post by jmvizanko on 2012-11-27
Well I managed to resize into the unallocated space using MiniTool Partition.  But I do have a 700 Gb HD, and it is now basically entirely comprised of my newly enlarged 470 Gb C drive, and the 210 Gb D drive.  So I'm pretty positive its not lying about size.

The question I have now, is can I do something about the size of that D partition, namely copy the files somewhere, shrink it to say 50 Gb, and then copy them back?  Is there the potential that there is crap there that will not show up in windows explorer?  Or should I just play it safe and be happy with the 220 Gb I just bought myself?  I suppose its really more of a Windows question, but the thing is, I can't remember whether or not that D drive was so huge before I used the Ubuntu CD to automatically resize partitions when installing Ubuntu.

---

### Post by StinkySQL on 2012-11-27
> **jmvizanko said:**
>  Is there the potential that there is crap there that will not show up in windows explorer?.

Very easily, yes. You do have the option of telling explorer (I think its in tools | folder options | views, then find the checkbox options in "hidden files and folders") that you want to stop hiding system files. Dangerous but perfectly OK.
 It is for ALL DRIVES  in the system so change it back when you are done so you don't accidentally delete something you need on your c: drive later. ;)

SS

---

### Post by Mark Phelps on 2012-11-28
> **jmvizanko said:**
> Now I am trying to resize my Windows partition.  However, when I fire up EaseUS Partition Master, my Windows C partition has a D parition in between it and what was my Ubuntu partition.  This drive is allocated a whopping 209 Gb, but all it has in it is a SamsungRecovery folder and 3 other crazily named folders that all only total 14Gb.  As far as I can tell, I cannot resize the C partition into the the unallocated Ubuntu partition, as they are separated by the D partition.
Partitions MUST be contiguous space, that is, they can't "jump over" another partition in their midst.  This is true of Linux filesystem partitions, as well, not just Windows.

> What are my options?  Can I resize "around" the D partition somehow?  
NO
> Can I merge the two partitions? 
Again. NO.
>  Can I backup D, blow it away, go about merging, and create it again (and if I do something like that, will I be able to use that recovery with the magic buttons at startup like I normally would be able to)? 
NO -- that "magic button" most probably relies on the Recovery partition existing and being intact.  IF you remove or tamper with it, you will not then be able to use it.

>  I can always just turn the Ubuntu space into an NTFS partition and have my hard drive "split in half," but I have to imagine there's some way to accomplish what I'm trying to do.

Not necessarily ... there is a HARD limit of 4 primary partitions on a drive.  IF you already have three and try to create two more, that will cause major problems.

Another thread mentioned that "peers" suggested using Partition Magic to do Windows partitioning. That's really BAD advice -- seeing as how that product hasn't been updated since 2003!

A much better solution is to go to the Minitool Partition Wizard site, download and burn their BOOT CD (using a Windows PC), boot into that, and use that to do partitioning.

As to the claim that messing around with partitioning in Windows risks loosing data -- that is most certainly true ... but then, the very same risks exist when messing around with partitioning in Linux.

---

