---
title: "If I reinstall Xubuntu will it wipe out dev/home?"
date: 2007-03-12
forum: Installation &amp; Upgrades
---

### Post by wulfhound on 2007-03-12
I like messing with Xubuntu - a LoT...perhaps too much.

Anyway, if I just want to reinstall it, is it save to just install Root again and keep the pointer to /home? I am not sure. Do a lot of files get installed to home? or is that basically just a catch all for personal files? Or should it be a practice to also rewipe your home partition (if you have one). Personally home and root are the same for me right now

What do you all do?

Thanks,

Sandaili

---

### Post by kokiri on 2007-03-13
not alot gets stored to home.
Just personal files (that you saved yourself) and preference files that would get redone when applications are launched for the first time.

I would back up all the files that I personally saved from home, documents pictures and the like and then just reinstall.

That's just me though.

---

### Post by Kateikyoushi on 2007-03-13
You could move home to it's own partition that way your personal settings and files are kept even if you reinstall the system. Here is a guide how to move to a /home partition. [LINK]("http://www.psychocats.net/ubuntu/separatehome")

---

### Post by confused57 on 2007-03-13
A separate /home is a good idea, but a separate data partition would be better for storing files( pictures, music, documents,etc).

---

### Post by Kateikyoushi on 2007-03-13
I store my data pictures music and docs in /home.
How would I benefit from having another partition for data ?

---

### Post by confused57 on 2007-03-13
> **Kateikyoushi said:**
> I store my data pictures music and docs in /home.
How would I benefit from having another partition for data ?
It's just my personal choice to have a separate data partition, some people prefer separate /home...I've just read there could be conflicts with configuration files in /home, if one wants to upgrade their version of Ubuntu and have possibly modified configuration files or various programs installed that might not be compatible with the newer version.  A separate /home should be just fine, I'm just the type that likes to err on what I "believe" to be the safer route.

Added:  I actually have both a small(20 Gb) separate home and a larger(100 Gb) ext3 data partition...talk about playing it safe.

---

### Post by wulfhound on 2007-03-13
> **Kateikyoushi said:**
> I store my data pictures music and docs in /home.
How would I benefit from having another partition for data ?

I am not sure :)  I think maybe in case someone accidently runs around in the terminal and accidently deletes home?? LOL...also what filesystem should it be? ext3? Fat32? Something else?

Thanks for the ideas, guys. I'm definitely reinstalling Xubuntu with a separate home. Here's my setup:

a 30 gig currently NTFS, with XP. I'm reinstalling XP (I have to share this computer with someone). I forget how much space XP really needs....but of course I'll give it the minimum to run. Can't windows be installed on a FAT32 partition? I'll look that up.

So, on the 30GB (the first booting HD) there will be an XP partition. I think I will also then   make a FAT share between XP and the xubuntu. 

The Xubuntu home and root and swap will be on the 100 gig. There's not much room on it, though. How big should root be? What if I install a LOT of programs? How big of a home partition should I have, and how big should root be? I've seen two different views about root - once I saw 5GB, others say a minimum of 10GB.

If I have a separate home and a separate partition for media (again, I am not sure what format it should be)...do I still need a swap partition? What kind of structure should that partition have???? I did mine with ext3. I just don't know.

What I do know is I want to get it all right so I don't have to format again for a while lol!!!

I know that's a ton of questions but hopefully someone might be able to explain. I understand all of it, and the basics, but I don't know what's best for my situation....

Sandaili

---

### Post by Kateikyoushi on 2007-03-13
Xp can run on FAT32, With all the updates it probably needs 7GB, depending on how big is your /documents and settings and pgoram files is can configure it.

You need more than 5Gb if you plan on installing gnome kde as well, if you know you need only xubuntu 5-6 GB is enough even if you upgrade to newer version.

Use ext3 for the linux partitions. 1Gb is enough for swap and the filesystem for that is swap.

---

