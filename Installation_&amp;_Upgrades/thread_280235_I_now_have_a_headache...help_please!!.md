---
title: "I now have a headache...help please!!"
date: 2006-10-19
forum: Installation &amp; Upgrades
---

### Post by funk99x on 2006-10-19
Alright, so for some reason I thought I'd give Linux a try. I'm trying to dual boot with windows. 

First I dowloaded the Ubuntu Live Cd and couldn't get my /root partion to be flagged as bootable. So, of course nothing was working. Then I read on these forums that trying the Kubuntu-Alternate cd might solve my problem, and for the most part it did.

Now I get to the first splash screen when Kubuntu is mounting the root file system. Then after about 4 minutes or so I get dumped to a shell saying /dev/hda2 doesn't exist. Hmmm, odd. So, I put the Ubuntu live cd and look have a look at my partions through GParted and my master HD is labeled as HDe. My slave is labled HDf and suprisingly my 3rd HD thats on my IDE card is labled HDd. Kubuntu had the hard drives label right and in order, A through C. 

So, now I don't know what to do. I assume GParted was telling me the correct labels for the drives? I remember trying to install linux years ago and it was horrid then. Sad to see things haven't gotten much smoother ](*,) . Hah, I'm probably just lazy and stupid :mrgreen: .

Any help is appreciated because I really want to get some experience on the OS.

---

### Post by gn2 on 2006-10-19
Have you read this thread: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by funk99x on 2006-10-19
> **gn2 said:**
> Have you read this thread: [http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

I glanced at it while I was searching the forums, but it didn't really help me, or so I thought.

I didn't realize dual-booting of the same HD was a bad idea. Kinda sucks cause now I'm not going to be using Linux. Heh. My HD setup doesn't really permit me to make a new partition for Ubuntu on my other drives. Either way this has been way too much of a hassle and I can see how it puts people off. Bummer.

---

### Post by h4rdwire on 2006-10-19
> **funk99x said:**
> I glanced at it while I was searching the forums, but it didn't really help me, or so I thought.

I didn't realize dual-booting of the same HD was a bad idea. Kinda sucks cause now I'm not going to be using Linux. Heh. My HD setup doesn't really permit me to make a new partition for Ubuntu on my other drives. Either way this has been way too much of a hassle and I can see how it puts people off. Bummer.

Its not a bad idea, It just takes time and patience to sit and watch other people's mistakes.  I run Kubuntu and windows 2000 on my laptop and had no problem installing what so ever.

I installed windows first and just made my partitions then, left a good amount for my ubuntu and boom, i get my grub option etc etc..working..I'm sure there plenty of threads on already with the same problems and same issues.

---

### Post by gn2 on 2006-10-19
> **h4rdwire said:**
> I run Kubuntu and windows 2000 on my laptop and had no problem installing what so ever.

I installed windows first and just made my partitions then, left a good amount for my ubuntu and boom, i get my grub option etc etc..working.

The problems usually come after the install, when you have a need to re-install Windows or have a kernel update, or decide to remove either OS or Grub just decides to become unco-operative.
.

---

### Post by gn2 on 2006-10-19
> **funk99x said:**
> I glanced at it while I was searching the forums, but it didn't really help me, or so I thought.

I didn't realize dual-booting of the same HD was a bad idea. Kinda sucks cause now I'm not going to be using Linux. Heh. My HD setup doesn't really permit me to make a new partition for Ubuntu on my other drives. Either way this has been way too much of a hassle and I can see how it puts people off. Bummer.

It's not having the two OS's on the one drive that's bad, it's having the MBR overwritten by Grub that's the probleem.

Much better to leave the MBR alone and install grub on a floppy.

---

### Post by h4rdwire on 2006-10-19
> **gn2 said:**
> The problems usually come after the install, when you have a need to re-install Windows or have a kernel update, or decide to remove either OS or Grub just decides to become unco-operative.
.

use the linux partitio manager and delete the windows parition and ur donE?

as far as ahving problems while doing a kernel update ill have to take ur word for it.

Removing either OS i would say keep it simple and use a partition manager from either OS, on windows u can use "Parition Magic", with linux i just use te boot CD and delete the parition windows is on .... should be ok that way.  But hey let us know what kind of problem your having, maybe ill be able to remember it in the near future if i have the same problem and it gets a solution here :-P

---

