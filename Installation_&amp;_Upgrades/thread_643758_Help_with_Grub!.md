---
title: "Help with Grub!"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by nogamal on 2007-12-18
I am a complete beginner and am trying to install ubuntu on a PC with a 100gb Hard drive partitioned into two drives - one "system" that has XP on it and programs, and one files with all my files (it's partitioned about 50-50). 

I formatted the "files" one (backuped first on an external, but wanted to keep my XP and the programs intact) and tried installing ubuntu on it from a cd i downloaded. however, at 94% it stops and says that grub could not be installed, and that this is a fatal error. I've tried searching for the solution, and even downloaded uspergrub cd and played around with it in the booting, but it generates "file error 15: file not found. booting 'not lucky'". 

Help!
I really want to be able to use ubuntu but not have to reformat my entire 100gb hard drive because I would like to keep the option of having windows available for a dual boot. why can I not install linux on my partition and how do I get grub to work?

I am really a beginner, so please answer in simple language..
Thanks for any help you can offer!

---

### Post by ajgreeny on 2007-12-18
Firstly, are you sure the CD you burned is OK, with md5sums that matched before and after the burn?  If so it may be worth trying deleting the partition you want to install on to before you do the installation this time.  I'm not sure why it should make any difference, but I think I have seen reference to it helping in other posts.  Give it a try.

---

### Post by nogamal on 2007-12-18
I deleted the partition from the XP Disk Management application - and I managed to install! Grub works fine. However, in XP I no longer see  that partition that I deleted. It only shows under "my computer" that I have a C drive and I'm missing my D drive with the other 44 gb. In the Disk Management application it says that the partition is there, but it's a "healthy (unknown partition)". I see it fine when I'm in ubuntu - it's just called filesystem and completely usable, but no longer so in XP. That is, if and when I copy my files and documents back into it, how will I be able to access it from XP? Is there a way to recover the partition without deleting the linux I already installed on it? I downloaded TestDisk but haven't used it yet because I'm afraid to damage the ubuntu, which I finally can use...

Advice?

Thanks so much for the help..

---

### Post by confused57 on 2007-12-18
This program should allow XP to see your linux partition:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by nogamal on 2007-12-19
Ok, that program is amazing, thank you!
And still, now I can see it in "my computer" and it has a letter assigned to it, but it won't let me open the drive - it says: "drive has not been formatted, format now?" - but it has all my ubuntu installation on it so I don't want to format it... but when I click "no" it just doesn't let me see the drive. Suggestions?

---

