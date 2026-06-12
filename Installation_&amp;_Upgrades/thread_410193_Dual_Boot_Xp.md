---
title: "Dual Boot Xp"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Eric the Red on 2007-04-15
I'm trying to dual boot. With Ubuntu / windows XP. With my last attempt I used Norton parition Manager while in xp (upon reboot I got the 'blue screen of death'). So I ended up loosing all my data in xp. :( 

After installing windows Xp again (sitting in xp right now), I'd like to know how I would install Ubuntu with a dual boot? Please, I don't want to mess up xp again. 

Any help would be greatly appreciated.

---

### Post by bulldog on 2007-04-15
Hi,well that is a long story :D 
I should first suggest to not use PM because it will give you troubles you don't want to have.
I suggest downloading and burning the GParted live cd,it's just 50MB so this is a matter of minutes.
If burned GParted,boot from this cd and you will have a nice partitioner with a graphical interface.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I presume you have only one hdd,on which you want to install windows and ubuntu.
Install windows first to the first primary partition,leaving enough free space for ubuntu,you need at least 10GB for ubuntu for a testdrive.

If windows is installed,boot the GParted live cd and resize the windows partition if necessary.
Create in the empty space,
One partition size 9GB for the root system which is called  / ,format it ext3
One partition for the swap file size 1GB ]similar as the windows page file] format it as swap
If you are satisfied,hit the apply button,and the partitions are created,this can cost some time though.
If done,exit the GParted live cd,and boot the ubuntu cd.

Follow the on screen steps,till you come to the partitioner,choose manual partitioning and mount the 9GB partition  as / (root) and set it to format again as ext3
Mount the swap as swap and format it as swap.
Continue the install,at the end it will install GRUB in the MBR,read carefully if it is as you want,windows and ubuntu to boot from GRUB [ubuntu by default but we can change it easily] and let it install,you need GRUB to boot ubuntu!!

Reboot and choose the desired OS you want to boot.

---

### Post by Eric the Red on 2007-04-15
I just was looking for some confirmation from other people, I really don't want to mess it up again. :o 

Thanks for your help.

---

### Post by Staff Monkey on 2007-04-15
I had some problems getting GParted to work on my machine due to bad sectors being detected.  I managed to find a Windows PE disk with Paragon Partition Manager that was a little more "assertive" with my Partition Table.

What I learned was that GParted is extremely careful with your drive.  If there's any problems whatsoever, it'll stop before it changes anything.  

I'd feel safe using GParted.  But back up your drive this time, and save any posibility of a problem.

Cheers.

---

### Post by Eric the Red on 2007-04-17
I have the Ubuntu live cd. 

So when I boot via the cd I get a menu:

"Start or Install Ubuntu"
"Start Ubuntu in Safe Graphics mode"
"Check CD for Defects"
"Memory test"
"Boot from first hard disk"

So I'm stuck on your instructions for here-> 

> 
If done,exit the GParted live cd,and boot the ubuntu cd.

Follow the on screen steps,till you come to the partitioner,choose manual partitioning and mount the 9GB partition as / (root) and set it to format again as ext3
Mount the swap as swap and format it as swap.
Continue the install,at the end it will install GRUB in the MBR,read carefully if it is as you want,windows and ubuntu to boot from GRUB [ubuntu by default but we can change it easily] and let it install,you need GRUB to boot ubuntu!!


Where do I go from the menu I wrote down?

---

### Post by confused57 on 2007-04-17
Have you seen this guide for installing with the desktop live cd?:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

don't hesitate to ask questions, if you're uncertain about any of the instructions in the link.

---

### Post by mocqueanh on 2007-04-17
Can i use GParted on USB instead for CD ?
(extract ISO to USB )

---

### Post by confused57 on 2007-04-17
> **mocqueanh said:**
> Can i use GParted on USB instead for CD ?
(extract ISO to USB )

You might want to do a Google search, but I found this method:
[https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29](https://help.ubuntu.com/community/Installation/FromUSBStick?highlight=%28usb%29)

---

### Post by lebadbob on 2007-04-17
Eric-

The dual boot should work fine. I used GPartEd to set up an ext3 partition, and a swap partition. After that, I used the alternate install disk (I've done this with 6.06, 6.10, and currently have 7.04 Beta) and did the install in text mode. 

I believe that the Ubuntu dual-boot installs are the easiest OS installs I have ever done. I have used many OS's for many years (DR-DOS, BeOS, MS*.*, and other flavors of Linux.)

Good Luck, Have Fun with it, and let me know if you need any help with it.

---

### Post by RonB123123 on 2007-04-24
Hi, I downloaded GParted and successfully planted the image on a CD. Booted up with it and it didn't have a graphical interface. For me, it had a command line interface and I was very confused and didn't want to type anything in, for fear of screwing something up lol. So I restarted and posted this. 

When I downloaded the file, these are the steps I took. I went to the gparted.sourceforge.net website. Clicked on Downloads on the left. Then clicked on "here" for the LiveCD. After, I scrolled down and downloaded this file "gparted-livecd-0.3.4-6.iso". Did I get the wrong file or something?

Can anyone help me?

---

### Post by confused57 on 2007-04-24
> **RonTheCon said:**
> Hi, I downloaded GParted and successfully planted the image on a CD. Booted up with it and it didn't have a graphical interface. For me, it had a command line interface and I was very confused and didn't want to type anything in, for fear of screwing something up lol. So I restarted and posted this. 

When I downloaded the file, these are the steps I took. I went to the gparted.sourceforge.net website. Clicked on Downloads on the left. Then clicked on "here" for the LiveCD. After, I scrolled down and downloaded this file "gparted-livecd-0.3.4-6.iso". Did I get the wrong file or something?

Can anyone help me?

I'm not sure what's going on, maybe you can try redownloading and burning another copy...I usually use a cd-rw disk and just reburn newer versions of gparted live cd iso on the same cd.  The iso that I downloaded was 44.9 Mb, if that helps any...make sure to burn at a low speed(8x or less).

---

### Post by RonB123123 on 2007-04-24
Hello confused57, 

I tried your instructions but the results were the same. I don't know what the issue is with gparted and me, but I will resort to using Paragon Partition Manager. It seems to be easier. 

Well here is what I have done so far in Paragon Paritition Manager. I resized my NTFS Partition (a total of 182 GB - Windows) and created 2 partitions. One 49 GB partition for Linux which is formatted as "Linux ext2" and another partition about 1 GB for swap and that is formatted as Linux Swap2. 

Is everything alright? Can I start installing Ubuntu without having windows deleted?

---

### Post by confused57 on 2007-04-24
> **RonTheCon said:**
> Hello confused57, 

I tried your instructions but the results were the same. I don't know what the issue is with gparted and me, but I will resort to using Paragon Partition Manager. It seems to be easier. 

Well here is what I have done so far in Paragon Paritition Manager. I resized my NTFS Partition (a total of 182 GB - Windows) and created 2 partitions. One 49 GB partition for Linux which is formatted as "Linux ext2" and another partition about 1 GB for swap and that is formatted as Linux Swap2. 

Is everything alright? Can I start installing Ubuntu without having windows deleted?

It would probably still be a good idea to backup any important data before you try installing Ubuntu, there's always a small possibility for problems.  I don't know anything about Paragon Partition Manager, but prepartitioning for Linux, using Partition Magic isn't usually successful.

What you might want to do is select "Manual" partitioning, select your 49 Gb partition, set to format as ext3, set the mountpoint as /, turn the boot flag on...then select your 1 Gb partition, set to format as swap.
Just make sure that your Window's partition ISN'T selected to be formatted & you should be just fine.

If you don't have a Window's install cd, you might want to burn a copy of the Super Grub Disk before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Maybe someone else can concur with what I've suggested or have a better idea?

---

### Post by RonB123123 on 2007-04-24
My Linux partition is formatted ext2, would it be safer if I formatted it as ext3? Because I really don't know the difference. But if it's safer, and if it will make less of a chance of having my XP removed when I install ubuntu, then I'll do that. But otherwise, it takes several hours to format things on my comp. Took a total of 3 hours to do what I said in my last post. 

I don't know how to set the mountpoint as / though. Should I do that using the Ubuntu Live CD when I install? I also don't know how to turn the boot flag on either, is it possible to do that also using the Ubuntu Live CD? 

By the way, thank you very much for your help. :)

---

### Post by bulldog on 2007-04-24
Ext3 is the default file system for ubuntu.
But don't you worry about that yet.
Just boot the live ubuntu cd and hit the start or install button.
You'll get in a live cd session and you can see if your hardware is properly working with ubuntu.
If you're satisfied,hit the install button on the desktop.

Now the actual installing begins,answer the simple questions and proceed.
When you come to the part which will let you choose were and how you want to partition your hdd,choose manual partition.
You'll get a list of your existing partitions.
Now choose the partition you made ext2 for ubuntu,and choose to mount it as  '/ '  which means the root partition.
Read all the options and set it to format  as ext3,and set the bootflag in the same menu.
If done,mount your swap partition as swap and format it as swap.
It's a little confusing when you do this the first time,take your time and read carefully  and you should be fine.
Be sure your windows partition is not set to be formatted though.

Proceed with the install and reboot at the end as asked,and enjoy your brand new ubuntu.

---

### Post by RonB123123 on 2007-04-24
Thank you Bulldog.

Im at the partitioning point. This is the window I'm at.
[http://img453.imageshack.us/img453/6131/screenshotinstalluk7.png](http://img453.imageshack.us/img453/6131/screenshotinstalluk7.png)

I right clicked on the ext2 and clicked on Edit Partiton. Another window popped up and I set the values to:
New partition size in MB: 52,600
Use as: ext3
Mount Point: /

Is that all correct? And for the Swap Partition, I am unable to check the little format box. I don't know why. When I right click on the Swap Partition and click on Edit Partition, these are its values: 
New partition size in MB: 1398
Use as: swap

Mount Point is disabled for it. Is that all correct? 

Sorry for all these questions. I just want to make sure Windows won't get killed in this process, because it has happened 4 times before. :(

---

### Post by RonB123123 on 2007-04-24
Could someone please help? I still have the update window open lol, and the Ubuntu Live CD has frozen on me before. Someone help before it freezes during installation... That's a real kick in the balls, because then ubuntu will be messed up and I would have to figure out how to remove it and then go through this crazy install. :(

---

### Post by confused57 on 2007-04-24
> **RonTheCon said:**
> Could someone please help? I still have the update window open lol, and the Ubuntu Live CD has frozen on me before. Someone help before it freezes during installation... That's a real kick in the balls, because then ubuntu will be messed up and I would have to figure out how to remove it and then go through this crazy install. :(
Have you seen this guide for installing with the live cd?:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

I've always used the alternate cd to install, so I don't know what specific advice to give you using the live cd.

---

### Post by RonB123123 on 2007-04-25
Yes I've tried that tutorial 3 times. And all 3 times, my Windows was shot down. Clearly, I'm doing something wrong. I just want to be sure if I'm doing everything correctly. Man, I really wish someone made a video tutorial or something showing how to do this correctly. 

Oh and that tutorial is a little out of date, since the partitioning windows are completely different in the 7.04 window. I really hope I get some info on my last post -- that's the last piece of information I need to install Ubuntu.

Edit: I got impatient and went for the install. Turns out, everything worked out fine. I remembered all the steps I took to get it to install as a dual boot with Windows, and I wrote downall the steps, so a screw up would be very very very unlikely the next time I need to install Ubuntu. :) 

Thank you all very much for your help!

---

