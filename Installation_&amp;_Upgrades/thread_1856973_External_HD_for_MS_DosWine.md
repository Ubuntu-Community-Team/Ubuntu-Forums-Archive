---
title: "External HD for MS Dos/Wine"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by Bobrm2 on 2011-10-09
I've three computers, two of which run Ubuntu, one I will be moving to the wood shop; it still has XP pro on it.

   I don't see why I can't but since I'm diabetic I need one MS program, and I wish to put it on a external HD and run the program through WINE. Not real familiar with Wine either.

  This computer, the one to run in the shop will also be wireless, and will have a minimal Linux operating system installed.

  What if anything do I need to watch for?

  Probably not difficult, but easy things sometimes bite you.

Bob

---

### Post by MAFoElffen on 2011-10-09
> **Bobrm2 said:**
> I've three computers, two of which run Ubuntu, one I will be moving to the wood shop; it still has XP pro on it.

   I don't see why I can't but since I'm diabetic I need one MS program, and I wish to put it on a external HD and run the program through WINE. Not real familiar with Wine either.

  This computer, the one to run in the shop will also be wireless, and will have a minimal Linux operating system installed.

  What if anything do I need to watch for?

  Probably not difficult, but easy things sometimes bite you.

Bob
I'm game on this.  Sounds like a potential challenge. (I like challenges.)

Okay You have 2 PC;s running Ubuntu, One PC running Windows XP.

You have one Windows program that you "Need" to use.

1. If you install WINE from one of your inside PC's, will that program run on it?  Tip, if you check the WINE website, if you look in their program database, someone may have already tried to install / run it and may have tips or say it can't be done.

 2. Running from external drive (probably eSATA or USB?) is not a probleem as you just mount it... fstab would mount that at boot.

3. And running the 3rd from the garage... wireless.  How far is it?  Wondering if it is in range.

---

### Post by Bobrm2 on 2011-10-09
Sounds like a potential challenge. (I like challenges.)

Okay You have 2 PC;s running Ubuntu, One PC running Windows XP.


It's an Accu-Check program I use to download the blood test results. It's able to download from the test meter to the computer. 
You have one Windows program that you "Need" to use.


Will check Wine web site.
1. If you install WINE from one of your inside PC's, will that program run on it? Tip, if you check the WINE website, if you look in their program database, someone may have already tried to install / run it and may have tips or say it can't be done.


Ok, so load the 
2. Running from external drive (probably eSATA or USB?) is not a probleem as you just mount it... fstab would mount that at boot.

The wireless distance is less than 100 feet. Have considered a booster. May not need one, will know after the move.'m game on this.
3. And running the 3rd from the garage... wireless. How far is it? Wondering if it is in range. 

Thanks will check the requirement/distances. Appreciate the help.

---

### Post by Cheesehead on 2011-10-09
Seem like there are two issues here:

1) How to run Accu-Check.

There are two answers to this. Wine or VM.
According to [http://appdb.winehq.org/](http://appdb.winehq.org/) , there is no data on newer accucheck applications. The older AccuCheck-Compass may work with a bit of tweaking according to the forums.

A Virtual Machine can handle this. For example, VirtualBox in the Ubuntu Repos cannot handle a USB connection, but VB from the Oracle download page can.

So try it in Wine first, and if that doesn't work then look into a VM.

2) Storage.

The windows application can be stored on your Linux filesystem, for example in your home or desktop directories, or any other you choose. Wine will still run it, and a VM will still run it.

Additionally, a VM can store the application on it's own virtual HD within your Linux HD.

If you are asking about external storage to ba able to move data around, then is there any reason an ordinary USB-stick drive couldn't work? That seems the simplest solution.

---

### Post by Bobrm2 on 2011-10-09
Cheesehead,
  The Accu-check compass is the program. and thanks for the great information. It will be next Wednesday before I can begin to use it, and I really appreciate your effort.

Bob R

---

