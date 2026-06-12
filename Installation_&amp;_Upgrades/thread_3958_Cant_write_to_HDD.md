---
title: "Cant write to HDD"
date: 2004-11-10
forum: Installation &amp; Upgrades
---

### Post by Grumpy on 2004-11-10
I actually have 2 problems with ubuntu 

1. When I try to create a directory on my HDD I get a message that I can  not write to the Hdd or when I download a program download manager say that the disk is full which cant be true I have an 80 gig hdd with only the OS loaded on it if my HDD is full then I am sorry but ubuntu is coming off my PC NOW.


2.If no fix for this then ubuntu is gone from my computer. I have dual 2.2 gig processors in my computer is there a smp kernel for ubuntu and where do I get it. It was not on the iso image I downloaded.

---

### Post by anklator on 2004-11-10
are u threatening us?? well... i know that there are smp kernels via apt or synaptic, its just the kernel you want plus -smp, anyways i think its better making you own one.

aboutt the hard disk, could u give more details?? i m not sure but it mighr be that u reached the filesystem max size, check quotas, check permissions on the dir u try to write, remember users only have write permissions on home dir, at last u can try making separate partitions

---

### Post by Grumpy on 2004-11-10
Naw I not threatening anyone just living up to my name Grumpy. Found the answer to the smp question now just need to find the answer to the writing to hdd prob. I thuink it is a mistake of mine but just need ideas on where to look for answer.

---

### Post by Joeb on 2004-11-10
[QUOTE=Grumpy]Naw I not threatening anyone just living up to my name Grumpy. Found the answer to the smp question now just need to find the answer to the writing to hdd prob. I thuink it is a mistake of mine but just need ideas on where to look for answer.[/QUOTE]


Where, exactly, on your hdd are you trying to write too?

---

### Post by Grumpy on 2004-11-10
Well I think I have found my problem and as I thought the problem was a loose nut behind the keyboard. I set up my partitons incorrectly. I had a 106mb /home partion and a 70.5gb / partition. Needless to say my /home dir could not accept a 768mb file that I was trying to download from the internet.

Like I said LOOSE NUT BEHIND KEYBOARD, as a CE for IBM I get more service calls for that kind of problem than I do for computers with real problems

---

### Post by anklator on 2004-11-11
root partition for ubuntu should not be so big, i think full install is 2-3 gb, so if u want to add more programs, it should be ok with 5-7 gb, and the rest on /home dir

---

### Post by Grumpy on 2004-11-11
yeah I know that set root to 10 gb and rest to home except for swap everything working GREAT so far I like this better than Fedora core 2 and Suse :smile:

---

### Post by anklator on 2004-11-11
this distro is working nice for me, its extremely simple to use, the only lack of ubuntu is that there are few packages only

---

