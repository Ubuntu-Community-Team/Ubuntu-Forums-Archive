---
title: "Too many partitions. Is there a way to overcome this?"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by dmacdonald111 on 2008-05-02
I would like to set up another partition for trying out the new version of Ubuntu. I totally understand the need for running it on a separate partition and keeping a working copy always. The problem I'm having is just that I have the following setup;

hda1 - NTFS
hda2 - Swap
hda3 - /
hda4 - /home

This is causing a problem as I wish to create a new partition to put the new version of Ubuntu onto, but in gparted, I am presented with a message saying that I have too many partitions.

Is there a way around this? Or will I have to use one of the other partitions (obviously the NTFS, but I would prefer not to).

TIA

Daniel

---

### Post by aheckler on 2008-05-02
Why don't you just use a LiveCD?

---

### Post by dmacdonald111 on 2008-05-02
I was using a LiveCD. I have the new Ubuntu version of it. The problem is having too many partitions.

---

### Post by aheckler on 2008-05-02
You said you wanted to "try out" the new version of Ubuntu. That's exactly what the LiveCD is for, trying it out. If the LiveCD appears to recognize all your hardware and so forth, then ahead and upgrade. If you are having some problems, then you should probably stick with whatever version of Ubuntu you have installed already.

---

### Post by chrisccoulson on 2008-05-02
The problem is, you can only have 4 primary partitions, which you already have. What you need is for one of your primary partitions to be an extended partition. On an extended partition, you can fit a number of logical partitions (which Ubuntu can be installed on, and increases the limit of 4 partitions that you're having difficulty with).

GParted can do this. Your difficulty is that you already have 4 primary partitions, so you'll need to delete one I think before creating an extended partition and then creating further logical partitions in it.

---

### Post by dmacdonald111 on 2008-05-02
aheckler, sorry, what I should have said was that I wanted to play around with it. Tinkering and such without ruining my current version of Ubuntu.

chrisccoulson, thank you. That was useful to know. I decided to format my ntfs partition as an easier way to get my primary partition. I never really used windows, but it was there like my stabilisers on a bike. lol. Time to take them off! \\:D/

---

### Post by aheckler on 2008-05-02
No need to apologize! :)

Also, if the specs in your sig are still correct, I'd try the 64-bit version of Hardy on your test partition. I have a 64-bit machine myself and 64-bit Hardy hasn't caused me any problems yet.

---

### Post by dmacdonald111 on 2008-05-02
Thanks! I'll take a look at that. Specs are the same :D

---

### Post by hal8000 on 2008-05-02
> **dmacdonald111 said:**
> aheckler, sorry, what I should have said was that I wanted to play around with it. Tinkering and such without ruining my current version of Ubuntu.

chrisccoulson, thank you. That was useful to know. I decided to format my ntfs partition as an easier way to get my primary partition. I never really used windows, but it was there like my stabilisers on a bike. lol. Time to take them off! \\:D/



The problem with primary partitions is that some operating systems insist on using them:- windows, solaris, freeBSD, syllable. If you intend on trying out anything else, make one of your primary partitions an extended partition.
In the extended partition you can create as many logical drives as you like... until libata came out. This limits the number of partitions to 15,
so its only a problem if you like to run a lot of alternative OS's.

---

