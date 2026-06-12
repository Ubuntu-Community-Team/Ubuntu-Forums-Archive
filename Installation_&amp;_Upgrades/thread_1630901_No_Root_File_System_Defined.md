---
title: "No Root File System Defined"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by HaGGardSmurf on 2010-11-25
[COLOR=Magenta]Edit: Ive figured out the mount point problem, but now I have an issue with swap space, scroll down to post #5 and 6 for more info.[/COLOR]

I'm trying to install ubuntu 10.10

I booted into ubuntu via a usb I created with the usb tool. I was playing around and decided I need to install this as its such an awesome OS.

Anyhow, I have 2 HDD's one is 300 GB and has xp installed, the other HDD I have is 750 GB and has win 7 installed. I want to dual boot Win 7 and Ubuntu while leaving the XP partition as it is.

Now I installed ubuntu but when I rebooted win 7 boot manager or whatever its called loaded up but did not show my ubuntu install.

So in windows I deleted the 2 partitions ubuntu had made (There was ~7gb partition and a ~150 gb partition) dont ask why, but I did.

Anyhow, now I am trying to install it, and I get to the partition to install it on, and I can see my 2 HDD's and all my partitions so I click my 150 gb of free space but get no root file system defined.

I googled it and someone had said they need a pic to determine what to do, so I made a video here it is: (Click to view video)
[[IMG]http://i140.photobucket.com/albums/r28/HaggardSmurf/th_VIDEO0015.jpg[/IMG]]("http://s140.photobucket.com/albums/r28/HaggardSmurf/?action=view&current=VIDEO0015.mp4")

---

### Post by libssd on 2010-11-25
It's an easy trap to fall into. Specify / as the **mount point** for the partition that Linux is to be installed in, and you should be off and running.

---

### Post by HaGGardSmurf on 2010-11-25
Jesus, I thought that said mouse point I was thinking what the hell does that mean.

Alright, I'll try that and report back in a little while thanks for the fast response!

---

### Post by libssd on 2010-11-25
> **HaGGardSmurf said:**
> Jesus, I thought that said mouse point I was thinking what the hell does that mean.

Alright, I'll try that and report back in a little while thanks for the fast response!
/ as mount point for root is one of those "intuitively obvious" things for people with Linux experience. :p Without, it's one of those WTF? things.

---

### Post by HaGGardSmurf on 2010-11-26
My new issue is I'm being told I have not selected a swap partition I have 5 gb of RAM do I need swap or not and how do I do it?

---

### Post by HaGGardSmurf on 2010-11-26
I've gone into disk utility and made a ~145 gb partition and named it ubuntu, and have a ~12 gb of free space.

How can I install ubuntu on thr 145 gb partition and use the 12 gb partition as swap space?

---

### Post by mcduck on 2010-11-26
> **HaGGardSmurf said:**
> My new issue is I'm being told I have not selected a swap partition I have 5 gb of RAM do I need swap or not and how do I do it?

same as with the root partition, you make a partition, set it's file system to "swap" and mount point to "swap".

While you probably don't need the swap for actual swapping with that amount of RAM, you should probably still have at least some amount of swap available.. Some programs simply assume that the user has swap, and might give you troubles if you don't. Besides, with the current hard disk size it's not a big deal to assign a gigabyte or two to swap.

Also the swap partition is used when hibernating the system, so if you wish to use the hibernate feature you should have at least as much swap space as you have RAM on the machine. (well, you really only need as much swap as you have *used* RAM, but I always assume that people are actually using all them RAM they put in their machines for something, so swap=RAM is a pretty good rule if you don't want nasty surprise when one day the machine is using a bit more RAM than it has swap when you try to hibernate... ;)

---

### Post by libssd on 2010-11-26
Swap FAQ here: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

If you have plenty of disk space, you may as well set up a swap partition = to your memory, even if it never gets used. I'm 99% sure that you cannot use Hibernate without a swap partition, but if you never plan to use Hibernate (I use Suspend instead), then create a minimal swap partitino of, say 512kb. Since upping my netbook to 2gb of RAM, I have never seen swap invoked, whereas it was occasionally used when I had only 1gb of RAM. Paging to swap slowed my netbook down to a crawl.

---

### Post by HaGGardSmurf on 2010-11-26
Alright, it all worked!

---

