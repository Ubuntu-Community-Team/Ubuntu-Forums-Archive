---
title: "[SOLVED] Hello. Dual Boot issue."
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by CMR_98823 on 2008-10-25
Hello all, I'm new to Ubuntu and these forums.

If this topic has already been posted for this issue, I apologize in advance.


I installed Ubuntu inside Win XP, and it was successful, at least to my knowledge. When I went to reboot and the OS selection screen appears, I select Ubuntu, but all that happens is my system will reboot again back to the OS selection screen.

Can anyone assist me and getting Ubuntu to boot successfully? 


TIA

- Roberts

---

### Post by melojo on 2008-10-25
try this
[https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20boot%20into%20Ubuntu)

> If Wubi fails to start, boot into windows, run chkdsk /r from windows on the same drive where you have installed Ubuntu, shutdown cleanly and then try to boot into Ubuntu again

---

### Post by CMR_98823 on 2008-10-26
I tried doing this, and it worked...kinda.

When it was finished scanning and rebooted, it came up to the OS selection screen. After I selected Ubuntu, an error occurred, didn't give me enough time to write down the error.

But then when it started loading Ubuntu, it came to a screen to enter a command, and I wasn't sure what command to put in, then I just rebooted and now I'm at square one again...does this possibly mean I'll have to restart the whole process?

TIA

- Roberts

---

### Post by CMR_98823 on 2008-10-26
Hello again, I am still having problems with booting.

I did however, uninstall Ubuntu to retry. 

I tried booting from the disc and it still will not allow me to select Ubuntu. Could it be possible that the disc I made is corrupt? I downloaded the ISO file from Ubuntu and mounted it to a CD-R.

Any help much appreciated.

TIA

- Roberts

---

### Post by melojo on 2008-10-30
its possible that it is corrupt, try burning at a slower speed.  I have some sony 700 mb cd's that for some reason will not burn the 8.04 iso, but I can use a dvd and it works fine.

---

### Post by CMR_98823 on 2008-11-02
Alright, thanks for the help. I'll give that a shot.

---

### Post by CMR_98823 on 2008-11-03
Still having problems booting Ubuntu.

I reburnt the OS to a dvd at a slow speed, the disc worked fine and this time actually asked me to specify which drive I wanted to install it to. So I selected my external HDD and everything was going smooth up until I rebooted. Then it started cycling back to OS selection screen.

After some thinking, I finally unplugged my HDDs other than my targeted drive thinking that would solve the boot issue. However, after I did that the only results I got were a blank black screen...I even set my HDD as a primary drive and I also switched it from mass USB storage device to an HDD.


I really want to get into Ubuntu, and this booting issue is driving me nuts haha. Any help would be much appreciated!





[EDIT 9:55PM]

Okay, I finally got it installed successfully, but then I went to boot and I got Grub Error 17?

---

### Post by caljohnsmith on 2008-11-04
So did you install Ubuntu inside Windows again, or did you give Ubuntu its own partition on your external drive? In other words, when you boot the Live CD, at the first menu did you select "Install Ubuntu", or did you select "Try Ubuntu without making changes", and then use the installer from the Ubuntu desktop? Also, do you get the Grub error 17 before seeing a Grub menu, or before seeing the text "Press ESC to see menu", or do you get the error after selecting an OS in the Grub menu?

If you can boot up your Live CD, use the "try Ubuntu without making changes", then open a terminal (applications > accessories > terminal), how about posting the output of:
```
sudo fdisk -lu
```
And we can work from there if you want.

---

### Post by CMR_98823 on 2008-11-05
I posted info in General Help. Thanks for your help. :)

---

