---
title: "Is windows affected at all by Linux/Ubuntu OS?"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by tram84mvp on 2009-12-07
I am an absolute beginner and i am downloading Ubuntu now, once i have the file and burn it to disc it says to put the disc in and restart your computer and follow the directions - no problem there, my question is: Windows will still be there and i can switch back to it after installing Ubuntu if i want - so Ubuntu is just an alternate operating system and it does not affect windows at all, therefore there is no danger of losing windows or having windows crash?

---

### Post by lisati on 2009-12-07
It depends on *how* you install Ubuntu. Included in your options are the following:
[LIST=1]
[*]Replace Windows completely -or-
[*]Use "Wubi" to install Ubuntu "within" Windows -or-
[*]Install Ubuntu along side Windwos inside its own partition
[/LIST]

Have a look here:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

---

### Post by aysiu on 2009-12-07
If you're downloading the Ubuntu Desktop CD and not the Ubuntu Alternate CD, then it will not affect Windows unless you specifically tell it to.

By default, it boots a "live" session than runs a fully functioning Ubuntu from the CD itself and your computer's RAM. It does not touch your hard drive until you click the **Install** icon.

Save yourself a CD, though, if you can boot from USB. [UNetBootIn](http://unetbootin.sourceforget.net) will help you "burn" the .iso to a USB key.

You can also use Wubi to install Ubuntu "inside" Windows as a virtual partition:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

---

### Post by cybrsaylr on 2009-12-07
I've been dual booting with Windows for 3 years now and Ubuntu never effected the Windows OS. Your PC acts like it has two separate and distinct OSs.

---

### Post by darkod on 2009-12-07
> **cybrsaylr said:**
> I've been dual booting with Windows for 3 years now and Ubuntu never effected the Windows OS. Your PC acts like it has two separate and distinct OSs.

Unless you use Wubi, so be careful with the decision. Wubi is easier to install for lots of people, but it does interact with windows, while the side-by-side proper dual boot is like cybrsaylr says.

---

### Post by dhavalbbhatt on 2009-12-07
> **aysiu said:**
> If you're downloading the Ubuntu Desktop CD and not the Ubuntu Alternate CD, then it will not affect Windows unless you specifically tell it to.




Just for my education - why would an alternate CD affect Windows, if you choose to install Ubuntu on a separate partition using an alternate CD?

BTW, I always seem to use the alternate CD for installing Ubuntu, and I do have a Windows partition and it never seems to have affected the Windows partition - or am I missing something?

---

### Post by gungrog on 2009-12-07
I've just installed 9.10 with Wubi, coz it's my first venture into Ubuntuland. ;)

The install was faultless, and Windoze is still there and functioning if I need it. 

I'd recommend this as a good choice for a total beginner, like myself.

---

### Post by aysiu on 2009-12-07
> **dhavalbbhatt said:**
> Just for my education - why would an alternate CD affect Windows, if you choose to install Ubuntu on a separate partition using an alternate CD? Well, in theory, if you know what you're doing and you have the laws of probability on your side, then it *shouldn't* affect Windows.

But the Alternate CD does **install** Ubuntu by default (it does not run a "live" session). And installation basically means either destroying Windows completely or resizing the Windows partition. The partition resizing process is again *theoretically* a non-destructive process. In reality, in rare cases, resizing a partition can result in data loss.

So I wasn't trying to say that necessarily by using the Alternate CD that you would be affecting Windows but that it involves a process that either deletes or limits the Windows' installation. The Desktop CD by default does absolutely nothing to the Windows partition or boot loader.

---

### Post by darkod on 2009-12-07
> **gungrog said:**
> I've just installed 9.10 with Wubi, coz it's my first venture into Ubuntuland. ;)

The install was faultless, and Windoze is still there and functioning if I need it. 

I'd recommend this as a good choice for a total beginner, like myself.

Wait until you do the updates. Read the threads about it and be ready. Especially this one, the solution is in post #10:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

As I said, very easy to install but I can't consider it stable when it's linux working inside windows. Besides, if your windows gets messed up, there goes wubi too.

---

### Post by darkod on 2009-12-07
> **aysiu said:**
> Well, in theory, if you know what you're doing and you have the laws of probability on your side, then it *shouldn't* affect Windows.

But the Alternate CD does **install** Ubuntu by default (it does not run a "live" session). And installation basically means either destroying Windows completely or resizing the Windows partition. The partition resizing process is again *theoretically* a non-destructive process. In reality, in rare cases, resizing a partition can result in data loss.

So I wasn't trying to say that necessarily by using the Alternate CD that you would be affecting Windows but that it involves a process that either deletes or limits the Windows' installation. The Desktop CD by default does absolutely nothing to the Windows partition or boot loader.

I completely understand what you're saying and you're making excellent point about Trying Ubuntu first, but in long term I believe the OP expressed desire to install Ubuntu so running it as LiveCD for longer is "out of the question", if I can use that expression loosely.

---

### Post by dhavalbbhatt on 2009-12-07
> **aysiu said:**
> Well, in theory, if you know what you're doing and you have the laws of probability on your side, then it *shouldn't* affect Windows.

But the Alternate CD does **install** Ubuntu by default (it does not run a "live" session). And installation basically means either destroying Windows completely or resizing the Windows partition. The partition resizing process is again *theoretically* a non-destructive process. In reality, in rare cases, resizing a partition can result in data loss.

So I wasn't trying to say that necessarily by using the Alternate CD that you would be affecting Windows but that it involves a process that either deletes or limits the Windows' installation. The Desktop CD by default does absolutely nothing to the Windows partition or boot loader.

I think that's the beauty of Ubuntu - it allows the user to do what they want. The alternate CD can be daunting for folks who are new (although they shouldn't be), but I think, if you know what you are doing, you will find the alternate CD a much better way to install - you are always in control, and I love that about Ubuntu!!!

Having said that, all my installs are using alternate CD and they have all worked very well for me (at least at the partitioning level - there have been other minor issues, but those were completely unrelated to this thread).

---

### Post by seenthelite on 2009-12-07
> **darkod said:**
> Wait until you do the updates. Read the threads about it and be ready. Especially this one, the solution is in post #10:
[http://ubuntuforums.org/showthread.php?t=1339203](http://ubuntuforums.org/showthread.php?t=1339203)

As I said, very easy to install but I can't consider it stable when it's linux working inside windows. Besides, if your windows gets messed up, there goes wubi too.

Thanks for this information I have a new laptop and was considering trying wubi, in the past on my older Laptop I have dual booted and had no problems.

---

### Post by rva1945 on 2009-12-25
> **darkod said:**
> Unless you use Wubi, so be careful with the decision. Wubi is easier to install for lots of people, but it does interact with windows, while the side-by-side proper dual boot is like cybrsaylr says.

I have already burn the Ubuntu 9.10 CD and it works fine. If I boot with it, I still can see all my Windows (XP) file system. Once I install the Ubuntu, wil I be able to choose between Linux or Windos boot? When in Linux, will I see the Windows file system?

---

### Post by SuperSonic4 on 2009-12-25
> **dhavalbbhatt said:**
> Just for my education - why would an alternate CD affect Windows, if you choose to install Ubuntu on a separate partition using an alternate CD?

BTW, I always seem to use the alternate CD for installing Ubuntu, and I do have a Windows partition and it never seems to have affected the Windows partition - or am I missing something?

I prefer manual partition and find the alternate-cd easier to use anyway, no desktop taking up all my RAM. I've not had any problems either albeit with Linux distros but if anything it's harder with linux - cfdisk reports windows as ntfs so easy to leave alone

> **rva1945 said:**
> I have already burn the Ubuntu 9.10 CD and it works fine. If I boot with it, I still can see all my Windows (XP) file system. Once I install the Ubuntu, wil I be able to choose between Linux or Windos boot? When in Linux, will I see the Windows file system?

1. Yes
2. Yes - but you'll have to reboot to switch between them
3. Yes - but the reverse is not true unless you manually pick ext2/3

---

### Post by rva1945 on 2009-12-25
> **SuperSonic4 said:**
> I prefer manual partition and find the alternate-cd easier to use anyway, no desktop taking up all my RAM. I've not had any problems either albeit with Linux distros but if anything it's harder with linux - cfdisk reports windows as ntfs so easy to leave alone



1. Yes
2. Yes - but you'll have to reboot to switch between them
3. Yes - but the reverse is not true unless you manually pick ext2/3

Thanks, I' ll like to say goodbye to Windows some day. I don't even consider accesssing Linux from Windows, I just don't want to loose any info I have stored in Windows.

---

### Post by sliketymo on 2009-12-25
It's possible that it could cause neglect,but that's another story! LOL.

---

