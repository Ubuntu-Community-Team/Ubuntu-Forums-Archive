---
title: "why does it recommend 32-bit?"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by 450rOOST on 2011-10-05
I am new to ubuntu and want to download to cd and try it out.  Why does it recommend 32-bit?  Would 64-bit not be faster?



Corei7, 8GB RAM.  I mainly use my laptob for editing helmet cam videos and watching movies.

Thanks.

---

### Post by TheNosh on 2011-10-05
64 bit support is dodgy at best. Some programmes offer it, others don't, and some do, but not very well.

---

### Post by 450rOOST on 2011-10-05
> **TheNosh said:**
> 64 bit support is dodgy at best. Some programmes offer it, others don't, and some do, but not very well.

awesome, thanks for the quick response.

---

### Post by Hakunka-Matata on 2011-10-05
Why not install them both, doesn't take long.  Just make an extra partition on your hard disk to accommodate a second OS.

---

### Post by 450rOOST on 2011-10-05
I want to keep windows 7 while I learn ubuntu, should I do the windows installer and run it along side windows.

I think I am going to put it on a cd and check it out first.  I tried out fedora last night on a cd, but what I want to try ubuntu.



This is a screenshot I took last night, fresh comoputer, pretty much nothing on it, 650GB to play with.  I'm backed up, but nothing partitioned yet.
[IMG]http://i678.photobucket.com/albums/vv143/RideRed/linux.jpg[/IMG]

---

### Post by pjd99 on 2011-10-05
> **TheNosh said:**
> 64 bit support is dodgy at best. Some programmes offer it, others don't, and some do, but not very well.
Horsepoop. 64 bit is fine.

32 bit is recommended so that people don't wrongly download the 64-bit version and then wonder why nothing will execute on their 32-bit processor.

---

### Post by sammiev on 2011-10-05
I have one laptop running 32 bit and the other two running 64 bit. This weekend coming all 3 will be 64 bit. As long you have have 4 Gib of memory you will have no problems and I must add one laptop only has 3 Gib memory and it runs as well as the other. :)

---

### Post by pjd99 on 2011-10-05
> **450rOOST said:**
> I am new to ubuntu and want to download to cd and try it out.  Why does it recommend 32-bit?  Would 64-bit not be faster?



Corei7, 8GB RAM.  I mainly use my laptob for editing helmet cam videos and watching movies.

Thanks.

If you do a lot of video encoding you'll want 64-bit. Should be faster.

And you have 8 GiB RAM, so the choice is install 64 bit or a 32 bit PAE kernel to get access to all your memory. A normal 32 bit system will only see 4 GiB max.

---

### Post by pjd99 on 2011-10-05
Link to article from 2009 (benchmarks from Ubuntu 9.04), where they said that 64 bit was just as stable as 32 bit (2 years ago). Includes some benchmarks. Pay attention to the ogg encoding, almost twice as fast.

[http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks](http://tuxradar.com/content/ubuntu-904-32-bit-vs-64-bit-benchmarks)

Another benchmark with 64-bit blowing away 32-bit: [http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)

---

### Post by pjd99 on 2011-10-05
And from the horses mouth: 
**Which Should I Choose?**

 Unless you have specific reasons to choose 32-bit, we recommend 64-bit to utilise the full capacity of your hardware.

Source: [https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)

---

### Post by 450rOOST on 2011-10-05
copy that folks, I'm going 64-bit.

I'm not going to try it on cd, I'm jsut going to install along side windows.  Does that mean that when I boot I will choose windows or ubuntu, or does that mean I will load ubuntu from windows?

thanks a lot for all the quick replies.

---

### Post by 450rOOST on 2011-10-05
would you recommend installing along side windows (I dont know what this does), or on a partition and boot via grub?

---

### Post by pjd99 on 2011-10-05
I've never installed inside Windows, so I won't recommend it. It looks like a good idea for those who are running Windows and don't want to mess with it. If you've got a clean Windows installation, I'd resize and install Ubuntu on its own partition.

---

### Post by thatguruguy on 2011-10-05
> **TheNosh said:**
> 64 bit support is dodgy at best. Some programmes offer it, others don't, and some do, but not very well.

I've seen exactly one program that does a poor job dealing with 64-bit libraries, and that is but one bug out of many for that particular piece of... software.

---

### Post by thatguruguy on 2011-10-05
> **pjd99 said:**
> Horse****.

That language is a bit strong for these forums.

> **pjd99 said:**
> If you do a lot of video encoding you'll want 64-bit. Should be faster.

And you have 8 GiB RAM, so the choice is install 64 bit or a 32 bit PAE  kernel to get access to all your memory. A normal 32 bit system will  only see 4 GiB max.

A normal 32 bit system actually sees something like 3.2 GiB, max.  Using the PAE expands the amount of memory that can be addressed, but does nothing w/r/t being able to run more threads. You are correct that video encoding goes markedly faster on a 64-bit OS, since most video encoding software (even ffmpeg) can make use of the multi-threading capabilities of a 64-bit processor.

---

### Post by 450rOOST on 2011-10-05
after taking a look at my current setup in an earlier post, how much space should I allocate for ubuntu?

---

### Post by pjd99 on 2011-10-05
> **thatguruguy said:**
> That language is a bit strong for these forums.

Apologies. I figured it's been acceptable since 2001 (as long as its not used in the literal sense): [http://en.wikipedia.org/wiki/It_Hits_The_Fan](http://en.wikipedia.org/wiki/It_Hits_The_Fan) :D

---

### Post by pjd99 on 2011-10-05
> **450rOOST said:**
> after taking a look at my current setup in an earlier post, how much space should I allocate for ubuntu?

How much do you want to give it? Minimum size I allocate for an OS (usually for VM's) is 20GiB, but 100-200 would be good if you think you can spare it.

Really depends on how much you want to use it. I primarily use linux, and my partitions are set up like:
```

/dev/sda1 -> NTFS -> Windows 7 -> 80 GiB
/dev/sda2 -> ext4 -> / (Linux root) -> 36.7 GiB
/dev/sda3 -> ext4 -> /home -> 71.6 GiB
/dev/sda4 -> Extended Partition
{
    /dev/sda5 -> Swap -> similar to virtual memory on windows -> 8 GiB
    /dev/sda6 -> NTFS -> /storage (D: on windows) -> 268 GiB
}

```

---

### Post by 450rOOST on 2011-10-05
sweet, while I'm bangin out questions here, do I want to setup my partitions with say, windows disk utility manager before I install ubuntu, or do I setup partitions as part of the ubuntu install.

Hey man, thanks a lot for responding, you could have told me to search a long time ago.  I have done some searching, but when I get someone like you on the line answering questions, I like to take advantage of the help, so thanks again.

---

### Post by pjd99 on 2011-10-05
> **450rOOST said:**
> sweet, while I'm bangin out questions here, do I want to setup my partitions with say, windows disk utility manager before I install ubuntu, or do I setup partitions as part of the ubuntu install.

Hey man, thanks a lot for responding, you could have told me to search a long time ago.  I have done some searching, but when I get someone like you on the line answering questions, I like to take advantage of the help, so thanks again.

Set them up as part of the ubuntu install. You will have to resize the existing Windows partition first (back up any important data first). I don't think windows will let you  (as it shouldn't) resize a mounted partition.

Some official looking info on resizing: [https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by sammiev on 2011-10-06
I tried along side of windows and booting by grub. To me Grub is the way to go. Should try it on CD first to make sure all is well with your computer. :) I set mine to about 100 Gib. :)

---

### Post by 450rOOST on 2011-10-06
gotcha.  OK, I know this was answered, but I'm dumb and need some further clarification.

Do I want to use the windows disk utility manager to get me that 100 gigs before I do the install.  Or when I'm installing will it ask me how much space to take for the partition.

I think I am going to go ahead and take 100GB via windows, then run the install.

---

### Post by pjd99 on 2011-10-06
> **450rOOST said:**
> gotcha.  OK, I know this was answered, but I'm dumb and need some further clarification.

Do I want to use the windows disk utility manager to get me that 100 gigs before I do the install.  Or when I'm installing will it ask me how much space to take for the partition.

I think I am going to go ahead and take 100GB via windows, then run the install.
The Ubuntu installer should be able to do everything you need. I doubt the Windows disk manager will let you resize an active (mounted) partition.

The link in my last post explains it in detail.

---

### Post by dino99 on 2011-10-06
[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by lisati on 2011-10-06
> **pjd99 said:**
> Apologies. I figured it's been acceptable since 2001 (as long as its not used in the literal sense): [http://en.wikipedia.org/wiki/It_Hits_The_Fan](http://en.wikipedia.org/wiki/It_Hits_The_Fan) :D

Wikipedia might like it, but we have a code of conduct here which frowns upon such things.

---

### Post by 450rOOST on 2011-10-06
> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

are three of those primary, or logical partitiions?

---

### Post by 450rOOST on 2011-10-06
> **450rOOST said:**
> are three of those primary, or logical partitiions?

nvm on that, moving along...

---

### Post by Elfy on 2011-10-06
I'd be inclined to let the w7 disk tool shrink it's partition , so long as it doesn't want to create dynamic discs.

Just shrink - leave the empty space unformatted and let the buntu installer deal with the rest of it.

---

### Post by 450rOOST on 2011-10-06
upon first startup, it said I do not have the hardware to run unity and would run classic.  What's up with that and what should I do?

---

### Post by westie457 on 2011-10-06
Hi this probably late in reaching you. If it is not to late and you have not installed your Ubuntu I suggest you take a look _[here]("http://ubuntuforums.org/showpost.php?p=11107302&postcount=5")_ for some advice on the partitioning.

It works.

Hope this helps and good luck.

---

### Post by Elfy on 2011-10-06
> **450rOOST said:**
> upon first startup, it said I do not have the hardware to run unity and would run classic.  What's up with that and what should I do?

Run classic for the moment.

Login, open a terminal and run 

```
lspci
```

post the output here

---

### Post by 450rOOST on 2011-10-06
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

smoker@smoker-Dell-System-XPS-L502X:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df5 (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Wireless-N 1030 (rev 34)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
smoker@smoker-Dell-System-XPS-L502X:~$

---

### Post by Elfy on 2011-10-06
Using Optimus I think - have a read here 

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Edit - I would certainly start a new thread to get support on that rather than use this one.

---

### Post by 450rOOST on 2011-10-06
I will search around the forum.  I assume I need to get some drivers or maybe not.  if I dont find anything I&#314;l start a thread.  Thanks

---

### Post by thatguruguy on 2011-10-06
> **dino99 said:**
> [http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)[]("http://ubuntuforums.org/showpost.php?p=10161428&postcount=2")

... except the OP noted that he was going to do a lot of video processing.  Again, there is a notable difference in the speed of video processing using a 64-bit OS vs. using a 32-bit OS. And I'm not just talking about high-end programs; I'm talking about programs like WinFF and handbrake.

---

