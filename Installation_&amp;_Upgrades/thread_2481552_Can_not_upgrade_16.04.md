---
title: "Can not upgrade 16.04"
date: 2022-12-02
forum: Installation &amp; Upgrades
---

### Post by KDMerrill on 2022-12-02
I have a 16.04LTS system that I'm trying to upgrade and having nothing but failure.  When I try through the Software updater, I get through the first step in the Distribution Window, then once it says Fetching complete, the window turns grey and just goes away.   I also tried via "sudo do-release-upgrade" and got the following:

Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease                       
Hit [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease                
Hit [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                     
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease               
Hit [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease             
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                       
Hit [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-security InRelease        
Hit [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) xenial-infra-updates InRelease         
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done

Restoring original system state

Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done
kevin@joker:~$ 

I'm at a loss on how to upgrade (broken DVD drive).

---

### Post by oldfred on 2022-12-02
Your 16.04 is EoL - end of life.
Regular Ubuntu 16.04 is supported until April 2021, but the light flavours, including Lubuntu, are only supported until April 2019.

Best to have good backups of your data & installed apps & do a new install of supported version. Better to use LTS versions.
If older computer a lighter weight flavor may be better choice as full Ubuntu expects newer systems.

I stopped using DVDs years ago. Converted to flash drives, but now have external SSD.
But most installs to internal drives are using ISO directly & booting ISO with grub2's loopmount. Boot from one drive & install to another.
I use Kubuntu 22.04 as stopped using gnome Ubuntu when they changed to Unity. But now they changed back to Gnome.

[http://www.ubuntu.com/about/about-ubuntu/flavours](http://www.ubuntu.com/about/about-ubuntu/flavours)

---

### Post by deadflowr on 2022-12-02
16.04 is still supported through the extended security maintenance infrastructure (esm)
which I see seems to be enabled.

What is it saying the upgrade release will be?
Is it offering an upgrade to 16.10 or 18.04?
I would expect it to be for 18.04, but one can never know for sure.

---

### Post by ajgreeny on 2022-12-02
I have moved this post to its own thread as it had no real link to the thread where you placed it.
Please do not hijack threads in this manner but start you own.  Even when you believe that your problem is identical to the one to which you added your post, 99% of the time it is not and the result is total confusion!

Now to your problem.
The difficulty you are seeing is probably the result of 16.04 now being out of support.
If you have not signed up to the extended support system for 16.04 updating in the normal manner is not possible, and even if it were, you could only move from 16.04 to 18.04, then from 18.04 to 20.04, and finally, if you wished from 20.04 to the current LTS version, 22.04.

As you can imagine this will be a very long term process and in my opinion is definitely not worth the bother.

I strongly recommend that you backup everything in your current home folder or partition, ie, your own personal files and folders, then clean install the new 22.04 version and finally restore the personal files to the new home.

---

