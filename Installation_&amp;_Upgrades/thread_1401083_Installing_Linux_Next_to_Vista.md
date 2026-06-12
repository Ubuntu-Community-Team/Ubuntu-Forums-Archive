---
title: "Installing Linux Next to Vista"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by emagine on 2010-02-07
Hello Linux Community,

I know this seems like a pretty simple concept, but I have been spending a ton of time on trying to successfully figure out how to install Linux Ubuntu 9.10 on my computer alongside Windows Vista.  Here is my situation:
I have a 140 GB hard drive with only Windows Vista installed and only one partition.  I have 50 GB free on my hard drive.  I also have about 9 GB of space "unallocated" which I believe is there because I deleted the HP recovery partition.  All I want to do is install Ubuntu, without getting rid of Windows.  I only wish to use Ubuntu for messing around with and installing some Linux software.  So I want a 30 GB partition for Linux.  I also do use sleep/hibernate/suspend and would like a swap partition and am not too concerned with a /home to save my settings.  Maybe in the future, but for now, I just want Linux on my system.
So, can I install it only using the Linux installation process which includes a partition editing step, or must I use a third party program to prepare for the Linux installation.  Thank you. I also have an image attached of my hard drive info (please look at).

---

### Post by zvacet on 2010-02-07
Defragment Vista few times and then shrink that partition to get 30GB of unallocated space.On that space install Ubuntu.You can do this with Ubuntu CD during installation or with [Gparted live CD.]("http://gparted.sourceforge.net/")If you are going to install Karmic then let your  filesystem be ext4.

---

### Post by emagine on 2010-02-07
> **zvacet said:**
> Defragment Vista few times and then shrink that partition to get 30GB of unallocated space.On that space install Ubuntu.You can do this with Ubuntu CD during installation or with [Gparted live CD.]("http://gparted.sourceforge.net/")If you are going to install Karmic then let your  filesystem be ext4.

Ok, thank you very much.  I still have a few questions but I think I got it.

1.) Is there any point to defragging vista more than once in a row.  I mean, if you defrag, then do it again right after, will that change anything?

2.) I use defraggler from piriform, and besides giving me the option to defrag my files it gives me the option to "defrag freespace" or "defrag freespace (allow fragmentation)".  Is it necessary to defrage freespace and if you know, what is the difference between allowing fragmentation and not.

3.)What does the unallocated space on my hard drive actually mean, does that mean my hard drive is actually 150 GB or does it mean that I am taking up(leaving open space) 10GB of space on my 140 GB hard drive?

4.) When you say shrink my vista partition to get 30 GB of unallocated space, does that mean I just shrink it by 20 GB because I already have about 10 GB of unallocated space free?
 
5.) I am installing Ubuntu 9.10, how do I make the file system for the new partition be "ext4" or does it do it automatically.

Thanks a lot, I can see by your "I Ubuntu, Therefore, I Am" title that you are highly experienced.  I really appreciate your help.  I really want to learn this stuff!

---

### Post by OrangeCrate on 2010-02-07
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by emagine on 2010-02-07
> **OrangeCrate said:**
> [http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

Thank you, this is very helpful.  But could someone please answer my questions above.

---

### Post by nerdtron on 2010-02-07
> **emagine said:**
> Ok, thank you very much.  I still have a few questions but I think I got it.

1.) Is there any point to defragging vista more than once in a row.  I mean, if you defrag, then do it again right after, will that change anything?

2.) I use defraggler from piriform, and besides giving me the option to defrag my files it gives me the option to "defrag freespace" or "defrag freespace (allow fragmentation)".  Is it necessary to defrage freespace and if you know, what is the difference between allowing fragmentation and not.

3.)What does the unallocated space on my hard drive actually mean, does that mean my hard drive is actually 150 GB or does it mean that I am taking up(leaving open space) 10GB of space on my 140 GB hard drive?

4.) When you say shrink my vista partition to get 30 GB of unallocated space, does that mean I just shrink it by 20 GB because I already have about 10 GB of unallocated space free?
 
5.) I am installing Ubuntu 9.10, how do I make the file system for the new partition be "ext4" or does it do it automatically.

Thanks a lot, I can see by your "I Ubuntu, Therefore, I Am" title that you are highly experienced.  I really appreciate your help.  I really want to learn this stuff!


1.) Not sure about that but you can try it if you have time.
2.) Go to the defraggler website and read there about what it does.
3.) Unallocated means its open, since it came from your hp recovery which you have deleted.
4.) Yes. But, my friend with Vista on her laptop also deleted her recovery partitions, about 10GB. And on the Disk Manager he can't shrink any of the laptops partitions. Weird. I don't know the case for you though.
5.) ext4 filesystem is used by default.

---

### Post by emagine on 2010-02-07
In this guide:
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

It says I should only change the size of the partition from within Windows.  Because in vista it "does not allow you to move the MFT (Master File Table)"  I am assuming this means I can't just shrink it during the installation, but I must do it before hand.  Is this correct?  Becuase zvacet said I could do it during the installation.

---

### Post by Mark Phelps on 2010-02-07
> **emagine said:**
> In this guide:
[http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes](http://ubuntuguide.org/wiki/Multiple_OS_Installation#Changing_Windows_partition_sizes)

It says I should only change the size of the partition from within Windows.  Because in vista it "does not allow you to move the MFT (Master File Table)"  I am assuming this means I can't just shrink it during the installation, but I must do it before hand.  Is this correct?  Becuase zvacet said I could do it during the installation.

Having wiped your recovery partition, and presuming you do NOT have a Vista recovery CD, you're taking a big chance using any Linux utility to shrink the Vista OS partition.  If anything goes wrong (and there have been LOTS of such cases), you will end up with no bootable Vista OS -- and no way at all to recover it.

So yeah, you CAN use whatever you want -- but you're safer if you use the Vista Disk Management utility to shrink it's OS.

---

### Post by jethrodaniel on 2010-02-07
I agree with Mark, but if you accidentally mess something up then torrent a download of Vista and use your valid product key to activate it (legal). It's simply another way to create a Vista backup CD/DVD

---

### Post by emagine on 2010-02-07
> **Mark Phelps said:**
> Having wiped your recovery partition, and presuming you do NOT have a Vista recovery CD, you're taking a big chance using any Linux utility to shrink the Vista OS partition.  If anything goes wrong (and there have been LOTS of such cases), you will end up with no bootable Vista OS -- and no way at all to recover it.

So yeah, you CAN use whatever you want -- but you're safer if you use the Vista Disk Management utility to shrink it's OS.
I do have all my files backed up.  But upon doing some research, I found this is the best way to shrink the partition:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
What do you think?

---

### Post by emagine on 2010-02-07
> **jethrodaniel said:**
> I agree with Mark, but if you accidentally mess something up then torrent a download of Vista and use your valid product key to activate it (legal). It's simply another way to create a Vista backup CD/DVD

Can you give me a link to a trusted torrent download of windows vista home premium 32 bit?  All the ones I have found look sketchy.

---

### Post by manzdagratiano on 2010-02-08
I have used Perfect Disk when I had Vista - to resize my C: drive. I can say with certainty that this was the only piece of software which led me to resize the C: drive without any errors whatsoever - it defrags everything to become contiguous, including the MFT, and then you can use the resize feature in Disk Manager - it will work, though one might have to repeat the defrag-resize cycle a few times. I was able to shrink my C: drive from 100GB (the naive partitioning the shrink volume feature led me to achieve in the very beginning) to 30GB using the same.

GParted can resize NTFS partitions fine; I just would not suggest risking the C: drive with it, since Windows is quirky.

As for installing Ubuntu alongside Vista, I have ONE suggestion - DON'T. Just get RID of Vista, and there is NOTHING there that Ubuntu will not do better. I did just that six months ago, and have not regretted a single day. And yes, the recovery partiton was terminated and absorbed into Ubuntu as well. (That I did using GParted, and it all worked fine).

---

### Post by emagine on 2010-02-08
> **manzdagratiano said:**
> I have used Perfect Disk when I had Vista - to resize my C: drive. I can say with certainty that this was the only piece of software which led me to resize the C: drive without any errors whatsoever - it defrags everything to become contiguous, including the MFT, and then you can use the resize feature in Disk Manager - it will work, though one might have to repeat the defrag-resize cycle a few times. I was able to shrink my C: drive from 100GB (the naive partitioning the shrink volume feature led me to achieve in the very beginning) to 30GB using the same.

GParted can resize NTFS partitions fine; I just would not suggest risking the C: drive with it, since Windows is quirky.

As for installing Ubuntu alongside Vista, I have ONE suggestion - DON'T. Just get RID of Vista, and there is NOTHING there that Ubuntu will not do better. I did just that six months ago, and have not regretted a single day. And yes, the recovery partiton was terminated and absorbed into Ubuntu as well. (That I did using GParted, and it all worked fine).

1.)Did you just get the Perfect Disk free trial?
2.)Also, what is the "resize feature in disk manager"? Is this part of Perfect Disk?
3.)Do you recommend using Perfect Disk over the steps in this article?:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Also, I agree, I have Linux on another system and it is awesome.  But there are certain windows only programs I need.  I may make the switch in the future, but not now.  Please answer the questions above, you have already been a great help!

---

### Post by Mark Phelps on 2010-02-08
> **emagine said:**
> I do have all my files backed up.  But upon doing some research, I found this is the best way to shrink the partition:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)
What do you think?

That's basically the "safest" way to shrink the Vista OS partition.

A variety of MS Windows-based partitioning tools can do much the same thing -- EASUS Partition Master is one of these and is (so far) a free download.

Some claim that GParted is "better" because it will allow a lot more shrinkage, but it does that by ignoring protections that MS built into their Disk Management utility.  In some cases, it works just fine, but in others, it renders the partition unbootable.  This can generally (but not always) be corrected by booting from a Vista repair CD and running Startup Repair a few times.  But, if you don't have such a CD, then you don't have a way to repair the partition!

---

### Post by manzdagratiano on 2010-02-08
> **emagine said:**
> 1.)Did you just get the Perfect Disk free trial?
2.)Also, what is the "resize feature in disk manager"? Is this part of Perfect Disk?
3.)Do you recommend using Perfect Disk over the steps in this article?:
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Also, I agree, I have Linux on another system and it is awesome.  But there are certain windows only programs I need.  I may make the switch in the future, but not now.  Please answer the questions above, you have already been a great help!

You just need to download the free trial of perfect disk, because you would use it only for the next couple of days again anyway. The page you refer to also cites perfect disk at the bottom, and I would suggest go for that instead of the other stuff they talk about. Perfect Disk can show you what the relative placement of data sectors is on your main drive. Defragmenting will lead to a massive compression in the first pass (it defragments the drive normally and then the MFT on the next boot) - after boot, you will be able to shrink your volume by a huge amount.

The resize feature I was talking about is in Windows itself - in Disk Manager. Right click on a partition and "Extend Volume" - it will lead to absorbing all the free space available - that is, the free space right next to the partition being extended. If the free space you obtained was not as much as you need, run perfect disk again and defragment everything including the MFT - you will get more free space. You can go on until the size of the C: drive is almost the same as the space occupied in your C: drive.

I suggested not using GParted because Windows has its issues with the MBR, and nothing but Windows itself should be allowed to screw with it - thanks to Microsoft and its fiefdom. Also, if you did away with your recovery partition, I would suggest leaving it alone at the moment, because in continuity it would come BEFORE your C: drive (it did in mine) - and not be able to absorbed in the other partition. Using anything to try to shift the C: drive to use that space is dangerous - I know from experience (you will have to FIXMBR etc later; that was XP - I did not bother experimenting with Vista).

Also, the few programs that you are talking about for Windows - Ubuntu has something or the other that works AT LEAST as good; nowadays even specialized software like Mathematica/Matlab/Autocad/etc is available for Linux, and it runs faster there. If you would tell me what software you are talking about, I may be able to suggest alternatives. The reason I am nudging you is because I once held the same opinion and dragged on with Windows alongside Debian for four years. Then I rediscovered Ubuntu and it was time to kiss Vista goodbye. I would go so far as to say that it offends me to keep paying to upgrade something like Vista to the next level, when I already paid for it when I got my laptop.

---

### Post by emagine on 2010-02-08
> **manzdagratiano said:**
> You just need to download the free trial of perfect disk, because you would use it only for the next couple of days again anyway. The page you refer to also cites perfect disk at the bottom, and I would suggest go for that instead of the other stuff they talk about. Perfect Disk can show you what the relative placement of data sectors is on your main drive. Defragmenting will lead to a massive compression in the first pass (it defragments the drive normally and then the MFT on the next boot) - after boot, you will be able to shrink your volume by a huge amount.

The resize feature I was talking about is in Windows itself - in Disk Manager. Right click on a partition and "Extend Volume" - it will lead to absorbing all the free space available - that is, the free space right next to the partition being extended. If the free space you obtained was not as much as you need, run perfect disk again and defragment everything including the MFT - you will get more free space. You can go on until the size of the C: drive is almost the same as the space occupied in your C: drive.

I suggested not using GParted because Windows has its issues with the MBR, and nothing but Windows itself should be allowed to screw with it - thanks to Microsoft and its fiefdom. Also, if you did away with your recovery partition, I would suggest leaving it alone at the moment, because in continuity it would come BEFORE your C: drive (it did in mine) - and not be able to absorbed in the other partition. Using anything to try to shift the C: drive to use that space is dangerous - I know from experience (you will have to FIXMBR etc later; that was XP - I did not bother experimenting with Vista).

Also, the few programs that you are talking about for Windows - Ubuntu has something or the other that works AT LEAST as good; nowadays even specialized software like Mathematica/Matlab/Autocad/etc is available for Linux, and it runs faster there. If you would tell me what software you are talking about, I may be able to suggest alternatives. The reason I am nudging you is because I once held the same opinion and dragged on with Windows alongside Debian for four years. Then I rediscovered Ubuntu and it was time to kiss Vista goodbye. I would go so far as to say that it offends me to keep paying to upgrade something like Vista to the next level, when I already paid for it when I got my laptop.

I think I am ok, because my hp recovery partition that I got rid of, is at the end of my C drive, not the beginning (see attached image).  So does that mean I am good?  Also, I would agree, Linux is awesome.  But two programs I really need are itunes, microsoft office suite, and carbonite (automatic backup software).  On my next computer I will not waste money on Microsoft office, but I am in high school now, so it is nice to be compatible with other people.  I admit also itunes is crap on a PC, but until I get a new computer and media device, I am stuck with it.  Also, I dont know of anything like carbonite available for Linux.

---

### Post by emagine on 2010-02-08
Forgot to attach image, here it is

---

### Post by emagine on 2010-02-10
Ok guys, I am having some trouble defragmenting on boot using perfectdisk.  I have emailed technical support and should be able to fix the problem.  In the mean time, I just want to confirm.  If I have one partition with vista on it, then about 30 GB of "unallocated space", can I install Linux on that "unallocated space" using only the installation cd.

---

### Post by Mark Phelps on 2010-02-10
If you've shrunk your Vista partition (and have since rebooted into it to ensure that it's still OK), then you can use the Ubuntu CD to install into the unallocated space.

As to the apps you want to use, iTunes doesn't work on Linux, MS Office does (with Wine) but not all the features work and stuff like Access does NOT work, found no listing for Carbonite in the WineHQ site -- which means it probably does NOT work.

While Ubuntu, like other Linux distros, can do pretty much everything that MS Windows can, it can NOT run all of the same apps. If you have a strong reliance on MS Windows apps, and are not able (or not willing) to learn how to use Linux alternatives, then installing and using any Linux distro is going to end in disappointment. 

In this case, dual boot may be the best option in that it will allow you to boot back into MS Windows when you need to use those apps.

---

### Post by emagine on 2010-02-10
> **Mark Phelps said:**
> If you've shrunk your Vista partition (and have since rebooted into it to ensure that it's still OK), then you can use the Ubuntu CD to install into the unallocated space.

As to the apps you want to use, iTunes doesn't work on Linux, MS Office does (with Wine) but not all the features work and stuff like Access does NOT work, found no listing for Carbonite in the WineHQ site -- which means it probably does NOT work.

While Ubuntu, like other Linux distros, can do pretty much everything that MS Windows can, it can NOT run all of the same apps. If you have a strong reliance on MS Windows apps, and are not able (or not willing) to learn how to use Linux alternatives, then installing and using any Linux distro is going to end in disappointment. 

In this case, dual boot may be the best option in that it will allow you to boot back into MS Windows when you need to use those apps.
Thanks Mark.  ya, understand that.  the reason I want Linux is not to switch from Windows, but to just have another OS.  It is fun using ubuntu and I want it on my system.

---

### Post by Kir_B on 2010-02-10
Before you do anything, read my write up, "[COLOR=#cc33cc][Steps I took to shrink my Vista partition]("http://www.linuxforums.org/forum/ubuntu-help/154447-solved-i-cant-re-install-ubuntu.html#post738502")[/COLOR]". I painstakingly wrote every step I took, in the hopes that it might help others not screw their vista. It worked flawlessly for me. It is the long SAFE process.

Good luck and I hope that it helps you. Kir_b

---

### Post by emagine on 2010-02-10
> **Kir_B said:**
> Before you do anything, read my write up, "[COLOR=#cc33cc][Steps I took to shrink my Vista partition]("http://www.linuxforums.org/forum/ubuntu-help/154447-solved-i-cant-re-install-ubuntu.html#post738502")[/COLOR]". I painstakingly wrote every step I took, in the hopes that it might help others not screw their vista. It worked flawlessly for me. It is the long SAFE process.

Good luck and I hope that it helps tyou. Kir_b

I understand the trouble you had to go through.  But the easiest solution is to install the free trial of perfectdisk and you can use it to defrag on boot so it can access system files before Windows starts.  It is great!  before i could only shrink the partition in windows disk management by 142 MB, after using the defrag I could shrink it by 50GB.  It defrags pagefile and even hibernate files.  it is the best alternative to all the steps you took.

---

### Post by Kir_B on 2010-02-10
Read the write up, it's in there. I took my vista partition from 250gb down to 120 gb, and have since taken the vista partition down to 50 gb {it doesn't get used for anything, other than music management for my mp3 player}.

---

### Post by emagine on 2010-02-10
> **Kir_B said:**
> Read the write up, it's in there.

O yeah, ok.  Thanks. Also, some questions before install,
How do I create a swap partition during installation and how big should it be?
Which file system should I use, ext3 or ext4?

---

### Post by Kir_B on 2010-02-10
> **emagine said:**
> O yeah, ok.  Thanks. Also, some questions before install,
How do I create a swap partition during installation and how big should it be?
Which file system should I use, ext3 or ext4?

 I used 2 gb of swap {I only have 1 GB of ram}. During installation it should ask that very question. How much swap you should have depends on how much ram you have installed in your box. I've read from some people that you should have twice as much swap as you have ram, but this warrants further research. I have yet to see my system use more than 1 GB, but my system might be an exception, as I have a strange Dell box that has issues that no one else in the universe is encountering. 

As to ext 3 or 4. I used ext3 as I have read of issues with ext4, but they might be ironed out now. Safe bet is ext3.
                           
Hope that helps. Kir_b

---

### Post by emagine on 2010-02-11
Thanks for all your help!!  NOW ENTERING DUAL BOOT CITY!!!!  Installation went very well.  Anyone interested in doing this I recommend going to this site:
  [http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

It will give you steps to shrink vista partition and give you a better understanding.  I really didn't follow these step, because if you look at the comments, everyone said they just used perfect disk, which is what I did.  All you have to do is defrag system files, which can only be done right when the computer starts, before windows loads.  Perfect disk will allow you to do this, one of the only defraggers that can. Be sure to restart computer multiple times after defrag and volume shrink so the computer recognizes the changes.  THANK YOU SO MUCH GUYS!!!

---

### Post by manzdagratiano on 2010-02-11
I am glad everything worked out and that perfect disk works for you! Have fun with Ubuntu...

BTW, whenever you change your mind to switch to Ubuntu completely... Openoffice is now as good as Microsoft Office... and Rhythmbox/Songbird/a bunch of other stuff support ipods.

---

