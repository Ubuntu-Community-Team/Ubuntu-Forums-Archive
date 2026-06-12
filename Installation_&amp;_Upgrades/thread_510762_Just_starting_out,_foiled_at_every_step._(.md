---
title: "Just starting out, foiled at every step. :("
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by irel on 2007-07-26
Well I started off by downloading the AMD64 version and burning the ISO to a disk.  After the loading bar finishes, it went to a blank orange screen with a distorted box in the middle.  I could move the cursor but that was all. I powered down the machine and tried it again, this time verifying the disk first. Everything was fine but I got the same problem.   After digging around these forums, I decided to try the alternative install cd. After making sure the iso was kosher with that hash checker, I tried it again. That locked up at the installing software part.  I dug around some more and found a fix for that.  Finally, I'm ready to go!  I get to the login screen, and I'm stuck at the same blank orange screen with distorted box that looks like it's trying to say ubuntu and makes me think it's a driver issue.   I dig around some more and I find this thread:

[http://ubuntuforums.org/showthread.php?t=488303&highlight=distorted+login](http://ubuntuforums.org/showthread.php?t=488303&highlight=distorted+login)

Awesome, a fix for this problem.   Except at the end where I'm supposed to type in "sudo nano xorg.conf"  It then tells me that sudo: nano: command not found.   :(   Was that a typo?  What is it supposed to be?  I found a list of linux cmd commands and I just can't find anything close.

I'm sorry if I sound frustraited. I was just really excited about doing this tonight and spent my whole night trying to get this solved.  I hate asking questions that I'm sure have been answered elsewhere but I just don't have the energy to look anymore.  I guess if I could just find out what should have been typed instead of nano I'll be happy.


In case anyone needs to know, I'm running an AMD Athlon64 3500, 2GB RAM, an Asus board with an nForce 4 chipset, an 7800GT, and an WD 80GB SATA 1.5 hard drive.

---

### Post by meyou on 2007-07-26
sounds like you lack nano.

sudo apt-get install nano

---

### Post by irel on 2007-07-27
If you lived in Toledo, I'd buy you a beer.   Thanks, that worked and I'm finally logged in. :)

---

