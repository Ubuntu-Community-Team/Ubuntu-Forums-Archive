---
title: "Dual Boot HP Pavilion DV6 1355dx"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by bsantos83 on 2011-12-19
I am looking to install Ubuntu on my laptop. I have downloaded Ubuntu 11.10 64bit and I have partitioned my hard drive 30GB for Linux. What hardware information will I need for the install? This is my first install (if you couldn't tell) and I am looking for some help.

Hardware-
Intel core 2 T6600 2.2GHZ
HM5000JI ATA hard Drive
GT20L ATA DVD ROM
WIFI LINK 1000 BGN 
generic web cam

Thank you.

---

### Post by 2F4U on 2011-12-19
You will need no hardware information for the installation process, only when the system is installed and you boot into your new desktop, there may be some points that need your attention:
- wireless, if you are using it
- graphics driver: open source vs. proprietary, if you have nVidia or ATI (Intel is included)
- special keys on the keyboard, if you use them
- suspend/hibernate/resume: often don't work due to BIOS or graphics card problems

Just a remark on your machine. HP laptops are known to be not very Linux friendly, so you may find some issues, not only with Ubuntu but also with any other Linux distribution.

---

### Post by coldraven on 2011-12-19
I have a HP Compaq 6715b and installs are easy.
I disabled the fingerprint reader in BIOS because I never used it and it would beep every time that I accidentally rested my hand there.
If you want to go for the automatic install option (as regards partitions) then I might do this:
Boot-up from your Live CD, choose "Try Ubuntu".
Run gparted and select the 30GB partition that you created.
Right click and select "Delete Partition", it will then show as "Unallocated".
Nothing permanent will happen until you click "Apply" on the top menu bar, so don't get stressed you can cancel anything that you are uncertain about.
My reason for doing this is that when installing Ubuntu will ask "Install alongside Windows" and will see an empty space just waiting to be filled.
Otherwise Ubuntu might see a 30GB partition that is formatted NTFS and then try shrinking the wrong partition which will take a long time.
That's my theory, I might get shotdown in a minute :)

just make sure that you are connected by a network cable to the Internet, answer some easy questions then go away for half an hour. When you return it will be done.

From memory the questions are like this:
What is your language?
What is your timezone?
Where do you want to install to? (In your case the answer is alongside Windows)
What is your keyboard? (You can test-type to check)
What is your username?
What is your password?

---

### Post by bsantos83 on 2011-12-20
So installed Ubuntu alongside windows with out a problem. Everything seems to be running good. Can any one give me a link to a starter guide?

---

