---
title: "I screwed up everything"
date: 2007-05-04
forum: Installation &amp; Upgrades
---

### Post by mrbulle on 2007-05-04
I just installed Ubuntu 7.04 on my external harddrive. Everything went just perfect. 
I have one internal hdd  250gb with one 50gb windows partition and one with 200gb other stuff. 
On the external I have one 150gb with stuff and one 50gb with Ubuntu. 
When I boot Ubuntu it will mount the 200gb internal and 150gb external with no problem. But the 50gb windows wont show up. 
If I try to mount it myself I get an error saying it is wrong filesystem. 
If I choose to boot windows in Grub I get error 21, It cant find my harddrive it says. 

I ran a check disk program from the xp install cd and it told me the hdd was totaly screwed. 

I think I did a mistake when I installed Grub.. instead of using the (hd0) is used (hd0,0). Can this be the problem? And it there any possible way to restore what I did?

---

### Post by seshomaru samma on 2007-05-04
> I ran a check disk program from the xp install cd and it told me the hdd was totaly screwed. 
totally? are there any more details? anyway this cannot be the result of a Grub installation or an Ubuntu installation because both were installed somewhere else.
> I think I did a mistake when I installed Grub.. instead of using the (hd0) is used (hd0,0)
personally I don't mind grammatical mistakes , English is not my first language . but in this case the sentence is not clear at all. What do you mean?
Anyway to reinstall grub -use the Live CD
1. Boot from a Live CD, 

2. Open a Terminal. 

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" . Replace the question marks in the next command with whatever your computer spited out in the last command :

5. Type "root (hd?,?)"

6. Type "setup (hd0)"

7. Type "quit".

8. Restart the system. Remove the  CD.

---

### Post by mrbulle on 2007-05-04
With find /boot/grub/stage1 I got error 15, file not found. :(

---

### Post by seshomaru samma on 2007-05-04
maybe[ this]("http://supergrub.forjamari.linex.org/") will help

---

