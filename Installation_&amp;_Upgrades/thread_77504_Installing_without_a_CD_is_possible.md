---
title: "Installing without a CD is possible?"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by mikesoft on 2005-10-16
Hello, ubuntu comunity forum. It's my first post here, and I'll try to be as clear as possible since english isn't my native language (spanish is).

First of all, I'm eighteen years old, from venezuela, my name is miguel and I wish to try linux for the first time, I've never had the chance to try it since now ;) so i hope you can help me with this.

Ok, now to the point. Yesterday, i downloaded the 5.10 ISO file by torrent. The download was really fast and everything was fine. Then, i was going to burn the image... yeah sure i didn't have any CD to burn it to (at the moment).

So, I got this idea, but i don't know if it will work, i can't get a CD right know, but i really want to install ubuntu and try it. I know, most of you right know would be thinking "why don't you just buy the CD..:???: " and yes, you're right. I will, but not today, tomorrow!

Ok, this is my idea on how to install linux without the phisical cd. I have 2 hard drives, a 80GB that I use for windows, and i have another 40GB that i want to use for the ubuntu, so i would have the two OS in differents drives. Oh yes, the 40GB drive is damaged, but it works, but that's not a problem because the ubuntu is just for evaluation (let just say that).

OK enough of the non-sense stuff, now to the problem. Is it possible, to extract the files from the ISO (ubuntu 5.10) that is on the drive where windows is running (with winISO or else) and just with partition magic (or some other application) make some linux partitions on the slave drive (native, swap and a 3rd one), where in the 3rd i would copy the files of the ubuntu cd, and, with a boot cd, or something else, start at a command line at boot and then type something like " E:\install.exe" so the 3rd partition will be like a cd-rom... is that possible?

Thanks, i hope you can help me! Please, try to tell me everything I need in case this idea is correct. If not, don't worry, I will buy some CDs tomorrow and install ubuntu as it's meant to be. Sorry for making this long, it will not happen again. Thanks again.

---

### Post by linkunderscore on 2005-10-16
I misread your post. I thought you were asking if you can install from images on your hard drive--which I am pretty sure you can, but if you are gonna get cd's tomorrow, you might as well wait because it would be lots easier.

---

### Post by mlomker on 2005-10-16
> Is it possible, to extract the files from the ISO (ubuntu 5.10) that is on the drive where windows is running (with winISO or else) and just with partition magic

I don't think there is any way to do that.

---

### Post by mikesoft on 2005-10-16
[QUOTE=mlomker]I don't think there is any way to do that.[/QUOTE]
why not? do you mean extracting the files inside the image? i can do that, as a matter of fact i already did it but i'm just waiting for someone that could tell me if the whole idea is possible. I think it is, i will just wait. Thanks anyway.

---

### Post by chunk on 2005-10-17
[QUOTE=mikesoft]why not? do you mean extracting the files inside the image? i can do that, as a matter of fact i already did it but i'm just waiting for someone that could tell me if the whole idea is possible. I think it is, i will just wait. Thanks anyway.[/QUOTE]

It is possible, but it is not easy.

---

### Post by mikesoft on 2005-10-18
well, i bought the cd and burn the image already, and i went quickly to install the breezy... more problems.

first it was a problem with the cd, some error.. i think it said something like "cannot find.."...mm... a file, i don't know which one sorry, but i though it was my fault because before burning it i added a folder to the image containing some appz for linux, like firefox, drivers, etc.

So, i downloaded the image again, because the old one was modified, so it wouldn't work, and then, i burn the image again and try. Everything was perfect.

Installation begin, partition to disk reach 100%, base files for the SO were copying BUT.... when it was like 60% the computer shut down by itself !!!! WTF!!! so i turned it on again, and tried again with the installation, and the same happened... i think is the hard drive, as it's damaged but works "fine", i won't be trying again with this drive.. i don't want my computer to damage again.. i think i'm going to install it in my recent drive, where windows is installed but i mean in a differente partition, so at install y guess i should do manually the partition stuff... Thanks for your help :)

---

### Post by mlomker on 2005-10-18
> I think it is, i will just wait. Thanks anyway.

You can't boot a PC to an ISO image.  You can set up a server that supports network booting and then boot an ISO through the network adapter, but that's not what you were asking about.  You'd need a second machine/server to accomplish that and it takes some configuration...assuming that your machine supports network booting.

One of the reasons that I use VMWare is because it does allow you to boot to an ISO, but it's a virtual machine and not a physical one.

---

