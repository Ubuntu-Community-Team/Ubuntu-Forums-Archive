---
title: "Installation Boot Failure"
date: 2011-09-13
forum: Installation &amp; Upgrades
---

### Post by TDalton on 2011-09-13
Issue 1
I recently posted in the newb forum regarding issues with partitioning drives after using OS-Uninstaller to remove windows from my ASUS laptop.

I decided to just reinstall ubuntu clean and fresh, since I have backed up all my essentials.

during the installation process, much after partitioning was done an what not, the installation was interupted. The notice said something to the nature of "failure to install boot GRUB"

It gave me three options:
1. install to another device
2. don't install 
3. cancel at the risk of the laptop not booting.

Neither of the three did anything, as the process seemed frozen. Clicking 'okay' on any of them did nothing.

I am now faced with attempting to reinstall at the risk of GRUB2 not getting put on the laptop. Any ideas?
Issue 2
I went to system options and hit suspend. The computer had a blank screen, but seemed to still run. It remained like this for sometime, before I turned it off. Why did suspend make my laptop a zombie?

I am now running ubuntu live CD.

Help on the matter would be awesome, as this is my only computer.

---

### Post by fdrake on 2011-09-13
> **TDalton said:**
> Issue 1
I recently posted in the newb forum regarding issues with partitioning drives after using OS-Uninstaller to remove windows from my ASUS laptop.

I decided to just reinstall ubuntu clean and fresh, since I have backed up all my essentials.

during the installation process, much after partitioning was done an what not, the installation was interupted. The notice said something to the nature of "failure to install boot GRUB"

It gave me three options:
1. install to another device
2. don't install 
3. cancel at the risk of the laptop not booting.

Neither of the three did anything, as the process seemed frozen. Clicking 'okay' on any of them did nothing.

I am now faced with attempting to reinstall at the risk of GRUB2 not getting put on the laptop. Any ideas?
Issue 2
I went to system options and hit suspend. The computer had a blank screen, but seemed to still run. It remained like this for sometime, before I turned it off. Why did suspend make my laptop a zombie?

I am now running ubuntu live CD.

Help on the matter would be awesome, as this is my only computer.

can you please using the live cd go to menu bar > applicatons > accessories > terminal and run this command:
```

sudo fdisk -lu

```
post here the results in your  next post.

after you have done this, go to this link end follow the instructions and post in a 2nd post the results.
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

