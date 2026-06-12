---
title: "Grub killed my Windows boot"
date: 2008-08-16
forum: Installation &amp; Upgrades
---

### Post by Firehalk on 2008-08-16
I already did had problems with **Grub vs Windows Boot**, but before was because I uninstalled it and it screwed with Win.

But what happened today was different.

I was really in the mood to make dual-boot with Linux again. So today - as I always did to install it - I made some unpartitioned space, booted with Ubuntu and pressed the install option on the dialogue. Then, I just selected "Use the most big unpartitioned space available". All correct, as far as I know.

I was able to reach my 2 Windows partitions, C:/ and H:/, within Ubuntu. So I thought was all fine.

But, when I tried to reboot and select Windows on the boot list, I got the classical "hal.dll missing" problem. I did had this same problem the last time too.

After lots of search and tries, I discovered Ubuntu did move my boot.ini (and 2 other boot files) to my second Windows partition (H:/) ! I have no idea what they were doing there, and the why it moved those files... Because C:/ is my primary, Windows is on C:/, H:/ is just some backup partition.

So after trying to edit menu.slt file, moving the boot.ini to my main Win partition, changing the entries on both files (hd0,1 and etc - I tried all), I did give up.

I'm really scared now to try it all again, but the fact is I want to migrate to Ubuntu little by little, and need that boot working.

Anyone has any idea of the why I have such troubles? And also, why Linux did move my Windows' boot files to my other partition?

Any comments over it would be really nice. So next time I can get over, or at least I can know the reason Linux did that.

Thanks, and sorry the long text.

P.S: I have one HD, and my Windows is XP Pro SP3

---

### Post by ad_267 on 2008-08-16
I'm not sure what caused your problem sorry, but I recommend next time using the manual partition option and use gparted from System - Administration - Partition editor in the livecd to make the partitions. You need to make an ext3 partition for ubuntu and a swap partition about twice the size of your ram. Then you can select these partitions during the installation.

This gives you a lot more control over what the installer does and where it puts everything.

---

### Post by Sef on 2008-08-17
Applications > Accessories > Terminal

```
Sudo fdisk -l
``` Small L.  That command will show the partitions.  Please copy and paste the results here.

---

### Post by manishtech on 2008-08-17
I want to give a very sound advice. While installing any Linux dont allow it to select its partitions itself. Explicitly mount the partitions before installing, this way you are sure what you are doing. 
You might be thinking that it would take the unpartitioned space, but by chance if it doesn't take then you may screw your system. I always goto manual partitioning, create partitions from free space, mount them and then continue the installation.

Always create two partitions, one for / partition where ubuntu will be installed, other would be swap where swapping and memory management would take place.

/ partition should be big as much you want to give to ubuntu and should be formatted with filesystems like ext3, jfs, reiserfs . If you don't have much idea use ext3

swap partitions should be formatted with swap filesystem. this should be theoretically double your size of RAM. But if you have more than 1GB of RAM, you don't need to have 2GB of swap. I have 2GB of RAM and swap is never used. I advice never to make swap partition bigger than 1GB.

---

### Post by Firehalk on 2008-08-17
Thanks a lot for all the answers.

Unfortunately I can't take screenshot or post it here, because I had to format. Now I just have Windows here.

I'm kind of newbie on all this Linux thing, so let me confirm things:

I have 2 partitions (C and H) under my Windows, as I said. Everything is occupied by those 2 partitions, right now. So, for me to create Linux partitions manually with the LiveCD, first I should let some unpartitioned space through Windows? Like, shrink my H:/ and leave some unpartitioned space from there or I can do this process through Linux LiveCD too? (I always did it when under Windows, never thought under Linux could do it too)

After that, under Linux - using that partition program - I create one partition as ext3 (which will be the main for Linux) and another as swap, which is twice the ammount of ram (I have just 1gb, so its better put 2gb? or just 1.5gb?).

And on the install, I manually select those 2 Linux partitions. That's it?

The only unclear part for me, is if its inside Windows or Linux that I create some free space first, for then create the 2 Linux partitions there.

Thanks a lot.

---

### Post by manishtech on 2008-08-17
You understood properly... Congrats..

I suggest shrink the H: partition by Windows if you are comfortable. Create free space enough for installing ubuntu and swap space and then boot from live CD.

You can goto System>Administration> GNOME Partition Editor, and create two partitions from there itself. One is ext3 one which will be mounted as / and another is swap. If you have 1GB of RAM, you wont be needing more than 1GB of swap unless you open many apps. I had 700MB of swap on 512MB RAM. Now after i upgraded to 2GB my swap isnt being touched by ubuntu

I think you main problem was to shrink via ubuntu or Windows. Do as you like or do as you feel safe.  :)

---

### Post by Firehalk on 2008-08-17
Thanks dude.

It's safe and easy to create these partitions manually under Ubuntu, before install? Or the probablity of something gets screwed is high?

I talked to someone that did it under "feisty" ubuntu distro, and that person told me that got some errors and wasnt able to do it.

Sorry for all these "scared person" questions, but the fact is... I'm really scared after all that happened.

I will set everything right here (since I had to format and lost some info), and later will give it a try :D

---

### Post by manishtech on 2008-08-17
> **Firehalk said:**
> Thanks dude.

It's safe and easy to create these partitions manually under Ubuntu, before install? Or the probablity of something gets screwed is high?

I talked to someone that did it under "feisty" ubuntu distro, and that person told me that got some errors and wasnt able to do it.

Sorry for all these "scared person" questions, but the fact is... I'm really scared after all that happened.

I will set everything right here (since I had to format and lost some info), and later will give it a try :D
I personally feel safer to do manually as you now what is happening and its all clear in front of you. With any other option I am sometimes unable to figure out which partition will be manipulated which can be sometimes a danger.

You might feel it scary in the beginning, but chill, unless you stumble you wont know how to walk. :)


Dont worry, nothing would happen. Something wrong would happen if your luck is bad, which has nothing to do with Ubuntu

---

### Post by Firehalk on 2008-08-19
Do you by any chance have some good tutorial about how to create those partitions manually, using gParted?

I was seeing some video tutorial in YouTube about it, but it messed up with my head. 

The guy says that needs to pickup the unallocated space (which I already did now here, I leaved 15gb of unallocated space. Did it using some Windows' program), click on "NEW" and set as "extended". And just on the "extended" partion, that I can set as **ext3** or **linux-swap**.

I thought it was just select the unallocated space, press "NEW", create the **linux-swap** with the ammount of space i want, and the rest of that partition i just let as **ext3**.

I know this is too amateur question, but can you (or anyone else reading it) help me with that? I need or no to "extend" the unnalocated space before creating swap and linux partitions?

> **EDIT:** With the help of some guy from other forum, I was able to install all fine. And guess what... Worked :D No more boot problem. Niiice. 

Thanks a lot to everyone here.

---

