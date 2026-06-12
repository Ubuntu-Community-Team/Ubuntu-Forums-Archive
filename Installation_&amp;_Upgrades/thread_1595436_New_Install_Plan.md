---
title: "New Install Plan"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by Cycledoc on 2010-10-13
I don't know whether to put this in the absolute beginner forum or here.  But since it involves installation I'm asking my question here.

I plan to change the size of my XP partition using Gparted, make a new partition in it's place and install 10.10 in the new partition.  That will give me a triple system computer (XP, 10.02, 10.10) for a while until I get all the idiosyncracies of 10.10 dealt with.

Will I have problems with this?  Pitfalls?  What do I do, if anything with linux-swap?

Many thanks

Cycledoc
Dell 2650

---

### Post by Mark Phelps on 2010-10-13
Don't understand the reference to 10.02.  Is that OSX?  Because, there is no Ubuntu 10.02 -- only 10.04 and 10.10.

And if it IS OSX, can't help you as I have no experience configuring Apple OSs.

---

### Post by Cycledoc on 2010-10-13
Sorry I meant 10.04.  I am currently dual boot 10,04 and XP.

---

### Post by lindsay7 on 2010-10-13
If you change the size of your xp partition you could have problems with Windows. I have done this and had problems and other times I did not.  If you do try this make sure that you defrag windows first and back up everything as in the worst case you will have to reinstall windows.  
If you can set up the ubuntu partitions a the root or "/" partition and set up a separate "home" partition that you can share with 10.4 and 10.10,  You can set up a extended partition which will hold the "home " partition and the "swap" partition. So would end up with a windows, 10.4, 10.10, and an extended partition containing the home and swap partition.

---

### Post by lindsay7 on 2010-10-13
here is my setup the sda7 is the 10.10 partiton and the fat partition is set up for files that windows and ubuntu can both read and write.

[ATTACH]172192[/ATTACH]

---

### Post by kansasnoob on 2010-10-13
In general that's a good plan IMHO. I multi-boot a lot performing testing (particularly iso-testing and upgrade-testing):

[ATTACH]172188[/ATTACH]

I know that would be major overkill for most people, but using a VM has limits, so I must eventually test on actual hardware.

Anyway you can see that all my OS's share the same SWAP. I prefer placing SWAP at the very end of my extended partition because moving or resizing SWAP will sometimes change it's UUID which creates a minor, but easily fixable, headache.

You'll also notice that I have three primary partitions and then an extended partition with many logical partitions. That's because of a 4 primary limit. (The extended counts as one primary.)

It's fine to resize XP with Gparted after defragging, just never move the beginning (left end) of your XP partition. Also, even though it doesn't apply to you, I always resize Vista and Win7 only with their own partitioning tools.

Ultimately it would be nice to see a screenshot of your setup in Gparted so we could give more specific recommendations, but this is a good general guide:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

The installer has changed somewhat but the manual partitioning option is still quite similar.

---

### Post by Cycledoc on 2010-10-13
Thanks for the replies.  

Attached is my current partitioning.  I plan to roll back the ntfs partition which has XP (Unfortunately I still need it to download audio books from our library--Overdrive software) and create a new partition between sda1 which contains XP and sda2 which holds ubuntu 10.04

i'm currently digesting the suggested references and will defrag XP before going ahead.  I'll let you know how I make out.

---

### Post by lindsay7 on 2010-10-13
In case we are not being clear, the reason you want to have your Ubuntu OS's on its own partition and a separate Home partition, is that when you update an OS or do a clean install of a new OS, you do it on the / partition for that OS and your settings and other info on the home partition is left alone.  This is much cleaner and a better way to go versus over writing the whole installation.

---

### Post by Cycledoc on 2010-10-13
I think I understand.  I'll be working on this the next day or two.  

Many thanks

---

