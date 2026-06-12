---
title: "Install of Software and GRUB Boot Loader Failing"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by D-Rick86 on 2008-02-08
Hey everyone!

I am trying to install Gutsy onto my Gateway Laptop. I have no OS on my system currently. When I run the text install from the alternate CD, I can't get the 'Installing Software' step to work. It fails at around 90%. So, then the insaller says I can try it again or come back to it. So, I tried to install the GRUB Boot Loader to the Master Boot Record (since it says something about it being ok since I don't have an existing OS) and that proceeded to fail also. I also couldn't get the LiveCD to work properly either.

What are my options now? Thanks in advance.

---

### Post by taurus on 2008-02-08
There are a few steps you could take.

1.  Did you do checksum of the ISO image after you've downloaded it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Did you burn it at a slow speed like 4x instead of a default speed of your burner or media?

3.  Did you pick the option on the first screen to scan the disc for defects?

---

### Post by Dennis Hogan on 2008-02-08
> **D-Rick86 said:**
> 
I am trying to install Gutsy ... from the alternate CD, I can't get the 'Installing Software' step to work. It fails at around 90%. So, then the insaller says I can try it again or come back to it. So, I tried to install the GRUB Boot Loader to the Master Boot Record (since it says something about it being ok since I don't have an existing OS) and that proceeded to fail also. 

I'm having this same trouble, with both the Ubuntu and Xubuntu alternate install CDs. It seems to be a similar problem to [this thread]("http://ubuntuforums.org/showthread.php?t=635244&highlight=e2fsprogs"), getting the same "resolver: package doesn't exist" errors for libnewt0.52. I've also got install failure for language-pack-en because of a dependency for language-pack-en-base which the loader can't seem to find (Ubuntu disc only; didn't get that far on the Xubuntu disc). Same as you, attempting to bypass to install GRUB (or LILO) gives me an error, and by this time, I'm out of time and having to go to work. 

Both discs were burned at minimum speed available for the computer they were DLd on (4x on the Ubuntu disc, 1x for Xubuntu), checksum-ed as valid, and checked for defects (clear).  Thread linked above seems to indicate that this is a known problem for Xubuntu alt-install discs.

---

### Post by Pumalite on 2008-02-08
In that thread the poster said it had 256 of RAM. Kubuntu might be too heavy of a Desktop.
256 of RAM or less>Xubuntu Alternate CD.

---

### Post by D-Rick86 on 2008-02-11
> **taurus said:**
> There are a few steps you could take.

1.  Did you do checksum of the ISO image after you've downloaded it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

2.  Did you burn it at a slow speed like 4x instead of a default speed of your burner or media?

3.  Did you pick the option on the first screen to scan the disc for defects?

Sorry for the late reply. Everything checks out. I used a DVD to do the burning on, should I try a CD and see if that yields another result?

---

