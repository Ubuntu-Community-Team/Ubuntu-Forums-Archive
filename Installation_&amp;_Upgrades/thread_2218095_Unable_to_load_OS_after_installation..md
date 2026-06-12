---
title: "Unable to load OS after installation."
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by josh45 on 2014-04-19
I have installed or tried to install a number of different versions of ubuntu with no success. Each has the same problem in that when I boot my computer, it will show the particular logo (eg xubuntu) for a few seconds and then go to black and (presumably) crash. It then does nothing. I have tried leaving my computer but it doesn't help. 

This happens when I attempt to "try without installing" from a Live USB, For versions where you can select "Install" directly from GRUB without trying, then the installation wizard will load and work without any problems. However, once I reboot after installation, then the problem described above will occur. 

I have been able to install and run Xubuntu 12.04 and Linux Mint 10 (although have problems with wireless with these: [see this thread]("http://ubuntuforums.org/showthread.php?t=2218099&p=12993736#post12993736")). I was able to update Xubuntu to 12.10, but when I then upgraded to Xubuntu 13, the problem described above occurred so I am having to reinstalling Xubuntu 12.04 for now. 

The versions of Linux that I have tried to install, and had the problem described above, are the most recent Lubuntu, Xubuntu and Ubuntu, the most recent Linux Mint and the most recent Linux Mint with XCFE. 

For the most recent Xubuntu, I then tried running Xubuntu 12.04 on a Live USB to run boot repair, but it did not resolve the problem. Unfortunately I did not record the number that it said to.

The computer I have is new. It is a HP Pavilion 15 n268sa that came with Windows 8.1 I got it a couple of days ago.

I would really appreciate any help with this because I have no idea what the problem could be. Thank you very much

---

### Post by Double.J on 2014-04-19
Hi there!

In case it hasn't already been said; a very warm welcome to the forums!

I wonder if it could be a graphics error? does the issue go away if you add "nomodeset" to the boot parameters? 

When booting, hold shift to get to grub, use the arrows to select the version to boot, then press 'E' and add 
```
nomodeset
```(if you have a list of funtion keys along the bottom of your grub screen, you can just pres F6 and arrow up to nomodeset)

Let us know how it goes!

Jj

---

### Post by david98 on 2014-04-19
As double.j press e and when you see text replace the words quiet splash with nomodeset this should help with a graphics issue if it is that which I quietly confident that it is. please let us know how you get on and if you solve the problem don't forget to mark the thread as solved.

---

### Post by josh45 on 2014-04-19
Thank you so so much! I did that for "Try Xubuntu" for the most recent version and it worked! Going to install it now. How do I make it so that it does that every time automatically, or if I just change it once installed it will stay like that? Thank you!

---

### Post by Double.J on 2014-04-19
Hi there, it often depends which graphics card you have?

Going out on a limb, here's the documentation for [nvidea]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

