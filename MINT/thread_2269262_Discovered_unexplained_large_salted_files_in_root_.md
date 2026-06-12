---
title: "Discovered unexplained large salted files in root folder, possible logger?"
date: 2015-03-14
forum: MINT
---

### Post by konrad6 on 2015-03-14
Hi all,

So I had Linux Mint running on my laptop, it's similar enough to Ubuntu so I'll ask here :p

It has a small hard drive, just 160gb, and I noticed shortly after installing the system, it ballooned to 80-some gigabytes full, even though I only installed a few common programs and had a few files, maybe 1-2gb worth. I looked through my home folder but there wasn't anything near that size. So over the past few weeks, I've noticed the hard drive getting more full on the order of tens of gigs, even though I wasn't downloading much of anything, and I clear my browser cache and other such files regularly.

I was determined to discover what was going on with the system, so I dug through all the directories the other day. I found in /root three suspicious folders with salted titles, that I knew nothing about. Here's a screenshot:

[ATTACH=CONFIG]260612[/ATTACH]

It looks as if two of the files are folders that appear to have 0 bytes with hundreds of thousands of items (????). I tried opening them, but after leaving my computer working on opening them for over an hour, it still hadn't loaded, meaning that there's some absurd number of files there. The third file shows 77.9gb, and it appears to be some sort of binary. 

My working theory is that this has to be some sort of malware that is saving keystrokes / screenshots / whatever to the disk, storing them encrypted, for later retrieval. I check my packets with Wireshark from time to time, and I haven't noticed anything abnormal, but sophisticated malware would stop transmitting as soon as Wireshark is turned on....

Does anybody have a better explanation as to what might be going on?

---

### Post by howefield on 2015-03-14
Thread moved to the "*MINT*" forum.

---

### Post by konrad6 on 2015-03-14
I think this fits much better in security, it's not a Mint specific topic.....

---

### Post by howefield on 2015-03-14
You are welcome to post your queries here, however the Ubuntu forums are primarily for Ubuntu and official flavours. We have provided this area for those who prefer not to post within their own community forums.

> Ubuntu Specialised Support
Specialised categories of support for the recognised Ubuntu flavours: Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, Mythbuntu and Ubuntu Mate.

---

### Post by Habitual on 2015-03-16
> **konrad6 said:**
> Does anybody have a better explanation as to what might be going on? Use Bleachbit?

---

