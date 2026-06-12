---
title: "Question about installing from Windows"
date: 2011-02-02
forum: Installation &amp; Upgrades
---

### Post by bkolb3923 on 2011-02-02
So I installed Ubuntu a few days ago using the windows installer so I'd have XP to fall back on in case I didn't like Ubuntu. However, I love Ubuntu and I now want to make it the only operating system on my computer.

So my question is this. Is it worth wiping my drive and reinstalling just ubuntu or should I just go with what I have now because it definitely works?

if there's not gonna be much advantage to doing all that I might just leave XP on my system and just run Ubuntu from now on. Also if there's a chance that my hardware isnt going to install or I'm going to run into other problems that I didn't with the windows installer then maybe I should just be happy with what I know works.

Thanks in advance for any help!

---

### Post by gordintoronto on 2011-02-02
How much disk space did you give Wubi? If you are at all tight on space, that will become an issue as you do updates, and system logs mount up. Both can be cleaned up, but it's easier if you don't have to worry about it.

Then again, making sure you have backed up every useful bit of data on your system is not a trivial chore. The first time I installed Ubuntu, I did it onto a new hard drive, and converted the old hard drive into an external USB drive.

---

### Post by Old_Grey_Wolf on 2011-02-02
WUBI has a maximum disk size of 30GB. Personally, I can use up 30GB quickly. WUBI is intended for trying out Ubuntu in order to determine if you want to install it permanently. I would not suggest using WUBI for a final solution.

I would suggest a dual boot of the Windows XP you have and Ubuntu while you decide if that is the OS you really want to use. Until you are familiar with Ubuntu and the way it rolls out releases, I would suggest installing the Lucid Lynx 10.04 Long-Term-Support (LTS) version. It will get security patches until April 2013. After you know more about the Ubuntu release cycles, you may choose to upgrade to another version.

---

### Post by bcbc on 2011-02-02
> **bkolb3923 said:**
> Also if there's a chance that my hardware isnt going to install or I'm going to run into other problems that I didn't with the windows installer then maybe I should just be happy with what I know works.

Thanks in advance for any help!You won't experience new hardware problems if you replace Wubi with a normal Ubuntu install. Wubi uses a virtual disk, but it directly runs off your computer's hardware (without virtualization).
Therefore, installing direct shouldn't cause any unforeseen problems.

I do advise backing up beforehand - "a few days" is really not that long and it's good to have a fallback if you need it.

---

