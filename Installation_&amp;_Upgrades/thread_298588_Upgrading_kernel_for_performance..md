---
title: "Upgrading kernel for performance."
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by budman21901 on 2006-11-12
I installed a new kernel for a P4 with HT.  (Used this howto [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192))  It says its installed, but grub did not give a line for it like the howto said it would.

I installed this kernel
sudo apt-get install linux-686-smp

checking only shows this.  How do i find out if this kernel is installed?  

budman@budman-desktop:~$ uname -r
2.6.17-10-generic

budman@budman-desktop:~$ uname -v
#2 SMP Fri Oct 13 18:45:35 UTC 2006

---

### Post by dcstar on 2006-11-13
> **budman21901 said:**
> I installed a new kernel for a P4 with HT.  (Used this howto [http://ubuntuforums.org/showthread.php?t=189192](http://ubuntuforums.org/showthread.php?t=189192))  It says its installed, but grub did not give a line for it like the howto said it would.

I installed this kernel
sudo apt-get install linux-686-smp

checking only shows this.  How do i find out if this kernel is installed?  

budman@budman-desktop:~$ uname -r
2.6.17-10-generic

budman@budman-desktop:~$ uname -v
#2 SMP Fri Oct 13 18:45:35 UTC 2006

Start Synaptic and do a search for it, if it is installed correctly it should appear in the Grub menu and allow you to boot it.

---

### Post by budman21901 on 2006-11-13
Ok, just did the search, and it's installed.  At the bottom of the menu it says 

"Obsoleted by: linux-image-generic
This package is for upgrades only."  

What does this mean?  Is this the reason i am not getting the kernel?  If so how do i go about getting a ugrade to this kernel?

---

