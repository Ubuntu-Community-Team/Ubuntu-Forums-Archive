---
title: "Extremely weird partition problem(Fiesty Fawn)"
date: 2007-12-19
forum: Installation &amp; Upgrades
---

### Post by shadow_dude on 2007-12-19
Hey, guys. I am having a problem with Partitioning my HDD to install Feisty, and a weird one. See, I tried to use Wubi to install(Unsuccessfully), but it did not do anything bad. I reinstalled it three times,and even tried Kubuntu once. But, I tried to redo it again. And THIS time, my computer goes crazy! It would go through BIOS, get to the "Ubuntu or Win XP" Screen, then reboot, and repeat, like it was a broken record. Both Win XP and Ubuntu did this. I decided to take the first Linux CD I could find(Which happened to be Linux Mint) and booted from it(Live CD). It said it could not display the contents, due to an "Unclean Shutdown", and said something about a "Force Command".

   I shut down Mint, and popped in my Feisty CD(BTW, I have a Gusty CD, but don't like it.), and it could read it, but it would give me a message that it "Could not display all contents of "Disk"", and I looked at the File browser, and I saw a couple of my folders, but not all. I double clicked into one, then clicked "Up", and I could see them all(This happens every time, it is random what appears). So, I have my windows files, and I was planning on getting an external HDD, backing it up, doing a clean install of Win XP, and starting over. But until then, I wanted to dual boot Feisty with my other files(and I guess the dead Windows). So, I go into G Parted, and tried to part. the drive, but it would not let me, because of an "Unclean journal". So now, I have this Ubuntu I can not install, and a dead copy of windows. Any thoughts would be appreciated.

P.S. I have already tried the F8/special startup options for Windows, so that is not an option.

---

### Post by TheWizzard on 2007-12-20
make a bootable rescue cd from: 
[http://rescuecd.sourceforge.net/](http://rescuecd.sourceforge.net/)

use e2fsck to check your hdd. repair if needed.

---

