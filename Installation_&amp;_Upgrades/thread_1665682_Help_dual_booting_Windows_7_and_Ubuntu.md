---
title: "Help dual booting Windows 7 and Ubuntu"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by murphy612 on 2011-01-12
Hello I'm new here as I'm sure you are aware and I was hoping someone far smarter than myself could help me out. I just don't understand how to dual boot both of my operating systems without having my Ubuntu partition broken up into TWO large ext4 partitions, an extended partition and a swap partition. However when I install Ubuntu on a completely empty drive, I only have ONE ext4 partition, an extended partition and a swap partition. Now I have completely reformatted my hard drive and it is ready for a clean install. Can some one please point me in the direction of a step by step guide (preferably one with lots of pictures lol) of how to install Ubuntu once Windows 7 is already installed and the volume has been shrunk to allow unallocated space for the Ubuntu installation. I had no problem with the Windows end of the situation. But once I run the Ubuntu installation cd I get to the the point where it says 1) install along other os, 2) use entire disk, or 3) set up partitions manually. Obviously the second option is not what I want. When I choose the first option a box comes up that is broken into two smaller boxes with a slider to choose how large you would like each partition. The box on the left says Ubuntu and the box on the right says Ubuntu 10.10. THAT PART CONFUSES ME SO MUCH! When I tried the third option to do it manually (advanced) I couldn't get it to boot at all. So please if anyone can help educate me with a sort of Ubuntu for Dummies type explanation and installation guide I would be so grateful. Just in case it's relevant I'm installing Windows 7 Ultimate 64 bit edition and Ubuntu 10.10 64 bit edition. If you need any other information to help me I'll gladly provide it asap. Thank you in advance to anyone for any help you can possibly be give me!

My computer specs are as follows:
Dell XPS 400
Intel Pentium D Processor
4 GB RAM
160 GB HDD (this is the one I'm trying to partition between the two operating systems)
1 TB HDD (this one is where I store all my personal files and has no operating system)

---

### Post by Gkri on 2011-01-12
> **murphy612 said:**
> [...] When I choose the first option a box comes up that is broken into two smaller boxes with a slider to choose how large you would like each partition. The box on the left says Ubuntu and the box on the right says Ubuntu 10.10. THAT PART CONFUSES ME SO MUCH! When I tried the third option to do it manually (advanced) I couldn't get it to boot at all. [...]

I am having the exact same problem here.

My problem [after this: [http://ubuntuforums.org/showthread.php?t=1664908](http://ubuntuforums.org/showthread.php?t=1664908) ] is that installation crushed, so when I try to re-install Ubuntu, I get what murphy612 says here.

What do we do?...

Is there a program that can "undo" the partation, in order to have again my whole disk in Windows? So then to try to install Ubuntu from the beginning?

---

### Post by murphy612 on 2011-01-12
I've been reading about it and watching youtube videos about it to no avail. I'm completely lost. Hopefully someone else who knows will see this thread and can help us.

---

### Post by kansasnoob on 2011-01-12
I prefer this method:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by garvinrick4 on 2011-01-12
Gparted is the partitioning software for ubuntu it is in the Ubuntu install cd
under Try Ubuntu and then System/Admin to gparted: Using this you can
make your own partitions and then install manually at installation.
Give it a read to understand what is going on with drive. Lots of gparted sites if googled.
Will look for a installation guide I have somewhere with pictures.

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by garvinrick4 on 2011-01-12
Hope this helps:

[Illustrated Dual Boot Site]("http://members.iinet.net/%7Eherman546/index.html")

---

### Post by murphy612 on 2011-01-12
I GOT IT TO WORK!!! Thank you so very much kansasnoob and garvinrick4. I can never thank either of you enough. I was becoming so frustrated because I couldn't figure it out. But then I looked at the step by step guides and it was all so simple to do. I'm so glad that there are people like you two on these forums that are willing to help desperate noobs like myself when we need it most. The two of you have my utmost gratitude. Thank you.

---

### Post by kansasnoob on 2011-01-12
I'm glad I could help a tiny bit.

It might be helpful to others searching the forums to mark this thread "solved" by using the thread tools :)

---

### Post by murphy612 on 2011-01-12
I know your last reply was two hours ago so it may just be that it hadn't updated yet when you last replied but it says that the thread is solved to me. Am I missing something kansasnoob?

---

### Post by kansasnoob on 2011-01-12
> **murphy612 said:**
> I know your last reply was two hours ago so it may just be that it hadn't updated yet when you last replied but it says that the thread is solved to me. Am I missing something kansasnoob?

Nope. I just didn't notice.

---

