---
title: "Gutsy does not detect WD hard drive"
date: 2007-12-01
forum: Installation &amp; Upgrades
---

### Post by nicklikesfire on 2007-12-01
So a while ago I posted about the fact that gutsy does not recognize my WD IDE hard drive.

Was this bug ever fixed? Should I re-download the 700 mb install file? or should I just intall gutsy on a new hard drive?

Thanks.

---

### Post by Pumalite on 2007-12-01
Is your drive recognized in BIOS? Have to tried to boot Gparted Live CD and see if it recognized your CD?

---

### Post by nicklikesfire on 2007-12-01
Sorry if I wasn't very clear in my original post.

Gutsy recognizes the other two hard drives I have installed. (I don't want to install the OS on either of them)

This is a problem with specific hardware that I'm using. Unfortunately I'm not very skilled with computers, so I really can't be of much use in identifying the specifics of the bug at this time.

This was discussed on this forum a few months ago. If someone knows if it's been solved, please let me know. (This would mean that the 700 mb install file on [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/) has been updated, so I should re-download it.)

If this bug hasn't already been fixed, I'm just going to install on a diffrent hard drive.

Please let me know, thanks very much!

---

### Post by Pumalite on 2007-12-01
You didn't answer my questions re BIOS and Gparted Live CD. I would like to help you but without more info I can't.

---

### Post by nicklikesfire on 2007-12-01
sorry about that,

I don't think the hard drive is recognized anywhere. I really don't know enough about ubuntu to answer your questions. yes, I am that uneducated.

I'm running Dapper Drake now. Ubuntu is installed on my 40 gig Western Digital HD. When I try to install gutsy on the HD, everything works up until the point where it asks me where to install to. The 40 gig WD HD is not listed as an option.

This is as far as I've gotten when trying to solve this problem.

I'm really not interested in trying to fix the bug or work around it. It is easier for me to just install to another hard drive (I already have one).

If no one knows if the bug has been fixed, or even if the main install file has been updated, that's fine, like I said, I have an alternate solution.

I really appreciate that people are willing to put time into helping me, so thank you.

---

### Post by mellowd on 2007-12-01
When you start your pc, can you go into BIOS and see if your hard drive is detected?

---

### Post by nicklikesfire on 2007-12-01
> **mellowd said:**
> When you start your pc, can you go into BIOS and see if your hard drive is detected?

I know it is detected now, as it is the hard drive that dapper drake is installed on.

---

### Post by mellowd on 2007-12-01
Downloads the Knoppix live CD. See if that can recognise your hard drive. If so you could use that to reformat your hard drive and try again from the ubuntu CD

---

### Post by aln on 2007-12-28
Same problem here :( I'm trying to set up my old PC (Western Digital 20 GB hd). It was running Ubuntu in the past without any problems. It's all messed up when I upgraded to Gutsy. Grub started to load always giving 22 or 15 error and never booted the system. I decided to reinstall using Xubuntu 7.10 alternate CD. Install goes fine up to the hardware detection moment : No hard drive detected. But hard drive is detected by BIOS, Knoppix, SystemRescueCD 0.32 and even my old Kubuntu 5.04 install disc. Really don't know what's wrong with Gutsy? (I've tested the install CD on another PC and it works fine). 

It seems like Ubuntu lost the support for old WD hard drives during the jump from feisty to gutsy??
Or is it something else??

---

### Post by Pumalite on 2007-12-28
Try this one for size:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
I'd advise you To get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it. Delete everything in your hard drive. Make new large partition of your whole hard drive. Format ext3 if you want. Then install Xubuntu.

---

### Post by aln on 2008-01-20
Thanks Pumalite, but that is exactly what I did using Gparted from SystemRescueCD. In the end the result was the same. Installer still didn't recognize the hard drive. Any other ideas?

---

### Post by Pumalite on 2008-01-20
DBan your hard drive then: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted as I told you.
(google bug of 7.10 with WD Drives)

---

### Post by aln on 2008-01-22
> **Pumalite said:**
> DBan your hard drive then: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then use Gparted as I told you.
(google bug of 7.10 with WD Drives)

Thanks again, but it still doesn't work. Guess it's time to fill in a bug report 
:(

---

