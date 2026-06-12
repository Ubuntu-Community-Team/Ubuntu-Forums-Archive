---
title: "Help with Ubuntu install"
date: 2007-03-19
forum: Installation &amp; Upgrades
---

### Post by KeeperMustDie on 2007-03-19
Hi, yesterday I installed Ubuntu and I was unable to access windows. Now I want to try reinstall Ubutnu correctly. Here is the situation:
  I have 1 hard disk witch is split in two partitions C: (5GB) and D: (70GB). C: is primary 
 and D: is logical. I want to install Ubuntu in C: and D: leave to Windows. Can anybody help me to install Ubuntu?

---

### Post by Scunizi on 2007-03-19
You might be able to install Ubuntu in 5 gigs but that's pretty small.  You have a lot of HD space on D.  What are you doing with that?  

... An install of ubuntu will create a minimum of two partitions, root (labeled "/") and swap.  Alternatively, you should typically have a home partition as a third to keep all your data, files, installs etc in one location for easier backup or in case you need to reinstall your system.  If you're not doing anything specific with the D drive and are just holding back space for data say so and you'll get better feedback on how to proceed.

---

### Post by KeeperMustDie on 2007-03-19
About 80% D: space is used. And I afraid that if I will install Ubuntu in D: and again will be unable to access to windows my all information will be lost. So I am request not a basic help.

---

### Post by Freiburg05 on 2007-03-19
Hi! 

    I'm not sure about what you did. Before installing ubuntu, windows was installed in C: or in D:? or you did the partions afterwards because of your problem to access windows?. 

     I'll try to give some ideas. May be this is a stupid Idea, but, if you had windows installed in C: and you installed ubuntu also in C: probably windows is not anymore there (although no data in D: should have been affected.). If so you have to reinstall windows. 
    
    If windows was installed in D: before it is still there, and the installation from ubuntu should recognize it. If it's so Ubuntu should also install GRUB boot loader and make a menu that at the boot time lets you choose the Operating System you want to boot.

      By the way, maybe 5GB is a bit curt to install ubuntu (you need around 1GB for the swap partition, so you have 4GB for Ubuntu files and programs. You will not have much place for your files.)
   
     May be you already thought about what I said, but if not hope it helps a bit.

---

### Post by KeeperMustDie on 2007-03-19
No Windows is in D: . Now I just testing Ubuntu and I don't need more space for it. I just need someone little more advanced then beginner to help me reinstall Ubutnu and if I will be unable to access Windows after Ubuntu reinstall I will just format C:. So, there is anybody who can help me to reinstall Ubuntu?

---

### Post by Freiburg05 on 2007-03-19
Sorry, I've only read the first post.

What about GRUB then? Is it installed? does it recognize windows?

---

### Post by Freiburg05 on 2007-03-19
ok sorry don't know why but my connection today it's pretty crappy.

---

### Post by KeeperMustDie on 2007-03-19
You can read more about my problem here: [http://www.ubuntuforums.org/showthread.php?t=387610&highlight=Help+new+in](http://www.ubuntuforums.org/showthread.php?t=387610&highlight=Help+new+in)
but I was unable to fix it so now I want to reinstall Ubuntu

---

### Post by Freiburg05 on 2007-03-19
I've read the other thread. You could try to install windows again in C: so you have windows in the primary partition. Then make a third partition using the free space in D: (supposing you have enough space free) and install ubuntu there.

    If you want to solve without touching partitions, I have no idea how. Sorry for not being more help.

 Bye!

---

### Post by buuntuu! on 2007-03-19
> **KeeperMustDie said:**
> You can read more about my problem here: [http://www.ubuntuforums.org/showthread.php?t=387610&highlight=Help+new+in](http://www.ubuntuforums.org/showthread.php?t=387610&highlight=Help+new+in)
but I was unable to fix it so now I want to reinstall Ubuntu

i suggest you take a timeout!
no offense, but reading this thread and the one you linked to, it seems to me that you have no idea of what you are doing... 
the simplest thing for you to do seems to be the following:
1. pop in your xp-cd and repair your MBR, just formatting your ubuntu-partition would leave you without access to window$ as it would delete your bootloader  (grub) too, which took over from window$' MBR when you installed ubuntu.
this step will leave you without your ubuntu-install, so backup any data you want to keep.
2. grow ntfs to full size again, so there is only one partition on your drive
3. reinstall ubuntu. during the install it will create all necessary partitions and you can decide how much space you want to dedicate to it...

BUT FIRST....
take a look at [psychocats]("http://www.psychocats.net/ubuntu/") page and read it thoroughly. there is all the info you will need.
good luck

---

