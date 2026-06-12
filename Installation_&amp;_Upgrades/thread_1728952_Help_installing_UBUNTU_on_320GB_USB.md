---
title: "Help installing UBUNTU on 320GB USB"
date: 2011-04-14
forum: Installation &amp; Upgrades
---

### Post by pawan98 on 2011-04-14
Hi, I have a 320GB Freecom Mobile Drive 11 Classic, I installed ubuntu on it using Wubi, however it is extremely slow, I need help installing it on my usb harddrive the proper way. Thanks.

---

### Post by Blasphemist on 2011-04-14
OK, here is one way.
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Look at this in the installation manual.
[https://help.ubuntu.com/10.10/installation-guide/i386/boot-usb-files.html](https://help.ubuntu.com/10.10/installation-guide/i386/boot-usb-files.html)

I quess I'd like to know what your full plans are for the drive. Will you have many distributions on it for installation and/or use? Will you use it for data recovery? Will you use it for normal external storage? 

You'll need to have a good idea on its uses to decide on partitioning and whether to use a casper r-w.

---

### Post by pawan98 on 2011-04-14
I'm planning to use ubuntu on it, because I don't have enough space on my computer.

---

### Post by Blasphemist on 2011-04-14
OK, that's a start. But you won't need all of this space for Ubuntu. First, how much space do you have on your internal hard drive? You'll get the best performance if Ubuntu is installed on that drive. What do you have on that drive now? Maybe if you need something can be moved off the internal drive to free up space for Ubuntu. You could then use the mobile drive for a variety of other things.

Do you plan to use the mobile drive connected to one or more computers? It's essentially a big USB stick. USB sticks are often used for things that wouldn't take advantage of the size of this drive. So you have to think of partitioning that you wouldn't for just a stick. I have an external USB drive and for me it is all about backup and redundancy. If your internal drive is very size challenged or if you have the desire to have your drive leave the desk, we could help better if you explain how you want to use it.

---

### Post by pawan98 on 2011-04-14
On my internal hard drive I a have 37.5GB hard drive, split into 2 partitions, a 24 GB one (:C/) and a 13GB one (D Drive/) (:C/) only has 500mb of free space on it, and has Windows XP installed on it. (D Drive) is also nearly fully, it has 5.5Gigs of free space. And no I don't intend to use this for other computers, just this one. The USB Drive can be partitioned, I don't really mind, as long as I get ubuntu on it :).

---

### Post by Blasphemist on 2011-04-14
I will start with the hope that others will jump in here. I haven't done what you are trying to do but have been thinking and looking around for what I can pass on for instruction. 

You should start with a backup but I have a feeling you would need to backup to this USB drive. Is that right? If so, the first step would be to partition the USB drive. I haven't quite decided on exactly how you should do that to allow it to end up with your Ubuntu installation on it.

What you want to do is unusual though I can see why you want to do it. There are tutorials for migrating from a WUBI configuration to dual boot but they are written as if you are installing to the hard disk, not an external USB hard disk. Your performance would be limited doing what you want to do, but it is now somewhat anyway.

One question is, do you need to keep Windows? What if anything is there that you can't do in Ubuntu now? It seems like installing Ubuntu to replace Windows and using the external USB drive to expand your storage is the best solution. Doing this would be as simple as copying your existing files to the USB and doing a straightforward Ubuntu install using all of the internal hard disk. I know you may need to keep Windows but I have to ask this.

Let me know what you think. I have to be away from the desk for an hour or so but as Arnold would say, I'll be back.

---

### Post by oldfred on 2011-04-15
Since you are also a windows user and may want to store NTFS windows data, I would make the first partition sdb1 NTFS and 50 to 100GB.

Then if you want a lot for Ubuntu:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Lots of detail, but not as complex as it may seem.
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

You do have to use manual partitioning to get the choice on where to install grub2's boot loader. Default installs just put the boot loader on sda which would overwrite your windows boot. You could still boot windows but only then with the external plugged in. Better to put grub on sdb (or whatever external is) and set BIOS to boot external first. If not there then it defaults back to boot your windows on the internal.


GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Shared NTFS partition - You can also use links
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by pawan98 on 2011-04-15
@Blasphemist.

Hi, Blasphemist, That'd be great if I were to install it on my PC and overwrite windows, but seriously, can you do everything on ubuntu that you can do on windows? What about when people give you a .exe file to install, it won't work on ubuntu, will it?

@oldfred. 

Hi oldfred, Thanks for the suggestion! :popcorn:

@lisahill

Hi lisahill, the thing is, so many people are giving me different methods I don't know what to do !

[B]However there is a 60% chance I will overwrite windows with ubuntu, if I can do everything from Windows on Ubuntu, including running .exe files.

Everyone - When is 11.04 gonna be released?
[/B]

---

### Post by Blasphemist on 2011-04-15
Thanks much Fred and Lisa for joining us. Your posts are both very helpful.

Pawan98, you do have a decision to make about Windows. You don't have the same luxury that many do, having lots of storage space on the internal drive. Many people, including me, have windows installed and taking much of the storage but very rarely being used. Windows takes 2/3 of my storage and almost never is used. There are no applications that I ever need windows for but that's not to say you are the same. Wine allows most windows applications to be run on Ubuntu but I never even use that. Linux and it's available apps fully meet my needs. Especially since you have XP, I think you should consider seriously killing windows. As for your friends giving you exe's, that is dangerous and I'm surprised you haven't run into version issues with only having XP but I don't know what they are giving you. I have Win 7 and am still about to kill it when my Kaspersky runs out in a couple months. I'll spend no more on Windows and it's needed apps and protection. But, Fred and Lisa have given such good help and the link to Herman's information is so easy to follow that you may want to to try Ubuntu on the external disk and see how it performs.

11.04 releases in two weeks. I use it now and have since alpha. From this I don't recommend using alpha versions but I learn much from working through the things that come up with beta versions. Others will tell you to only use long term support releases but they are much less curious and anxious to learn than me. I recommend to look into Wine and think about the what, when and why of the exe's you get.

Fred and Lisa gave you the opposite kinds of help while both giving you good instruction. Fred passed on very detailed and specific instruction and it is clear he knows this very well. Lisa gave you clear and concise steps to do what you need that also shows she knows this process well. Her instructions seem to be cut off.

Installing Ubuntu to this drive will limit performance as disk access is slower than for an internal drive. I did see another post in these forums from someone with natty running from an external that is quite happy. His user name here is jipbuntu. 

If this external drive is your only one, I believe it will be /dev/sdb1 but you can verify that as they describe. Fred has good advise on partitioning. GParted is a very good program to use for partioning. The link Fred included from Herman is great information. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html) I wish I'd seen this before and will be using it myself at some point for sure. Lisa and Fred both gave you information for use in the manual partitioning step, as does Herman. Herman's information could hardly be clearer nor more detailed, a rare feat. I like Fred's recommendation to put the Grub 2 boot loader on the external drive. As he says, if it is connected it will be your boot manager and if it isn't plugged in, your normal windows will boot.

From looking into this with you, and from what Fred and Lisa provided, I have learned a lot. With Herman's instructions I have no doubt you can do this with little risk as long as your focus is good. I have no doubt it will be I just mean that as a reminder. When you see that people have had terrible issues, often they just weren't paying close attention.

Good luck and let us know what you think and how it goes.

---

### Post by oldfred on 2011-04-15
I still have my XP on an old drive. I used it for Quicken which I have just about converted to kmymoney (not as complete but usable) and Turbotax ( I do not use online versions). 

I also use wine for the windows version 3.8 of Picasa, but Google worked with the wine folks to make a Linux version that used wine. But many newer windows programs do not work in wine. You have to check and many only work at some level.

We often see users who come back and want to add windows back on again. I would not suggest eliminating windows unless you have used Ubuntu a lot. There are many equivalent programs to just about everything in windows, some better, some equal and some not so good and depending on your exceptions Those may not be good enough.

---

### Post by pawan98 on 2011-04-15
Hello Blasphemist,

Thanks for replying, I think it may be best if it were to be fully formatted to UBUNTU, and I think I will do that, Thanks for the help :D. So I will have a 37.5GB partition, dedicated to UBUNTU, with a 1.2GB RAM, is that fast? Is that good? :DDDDDDDD

---

### Post by Blasphemist on 2011-04-15
Sounds good to me! As Fred said in his last post, only you know if like me you can loose windows. If you've been on Ubuntu long enough, you do know that. 

I recommend that you make a copy of your home directory from Ubuntu and your windows equivalent, to the external drive. You could use GParted in Ubuntu to partition part of the external for this purpose before you start the rest. You may have to install GParted from the software center. Then when you install Ubuntu erasing the internal drive you can copy back you documents, music, video's, pictures and templates. 

Ubuntu will create two partitions the second being a swap and that is good for your performance. If you feel adventurous and confident in the external drive (and I think you are confident in it), you could use herman's instructions for how to manually partition and put some things on the external drive. You might want to put home on the external for instance. Herman's instructions discuss and describe this. The option during installation for this manual process is at the allocate disk space screen and is listed as Something else if you are using natty. Herman's instructions show it from a previous version. 

I use natty and if you start from the beta it will automatically update to the release version as we get to that in two weeks but you may not want to jump into the new, it's up to you.

Let us know how it goes.

---

### Post by pawan98 on 2011-04-16
Oh great... the USB adapter doesn't work on UBUNTU. It says it doesn't find any networks.

---

### Post by oldfred on 2011-04-16
If computer is more than about 5 years your BIOS probably does not support USB boot. Is it then defaulting to network boot as next choice in BIOS? Your internal hard drive should be before network boot.

---

