---
title: "17-generic and 14-generic on GRUB, only 14-generic works"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Giltrap on 2010-01-27
Hello,

**Novice Alert:** I'm rather new to Ubuntu. I've played about with Live CD's and sort of got it working on a PS3, but that's about it. Now, my problem.

Basically, what happened is that I installed Ubuntu 9.10, and then I installed whatever updates it wanted, and then ...17-generic pops up, but doesn't do anything other than load up a terminal type thing full screen.

Here's everything GRUB says.

> GNU GRUB version 1.97~beta4

Ubuntu Linux 2.6.31-17-generic **<- This one doesn't work**
Ubuntu Linux 2.6.31-17-generic (recovery mode)
Ubuntu Linux 2.6.31-14-generic **<- This one does**
Ubuntu Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows NT/2000/XP (loader) (on /dev/sda1) **<- This one is why I installed Ubuntu :P**

I'm pretty sure it's supposed to be part of the updates I did, but to be completely honest I'm not even slightly certain.

I don't know if there's any more info you'd need from me about my computer, but if there is could you tell me how to find it. Thanks.

So the questions I'm asking really:
Is meant to be an updated version?
and if so, How do I make it do what it's meant to do?

Thanks!


*Semi-related: After installing Ubuntu my Windows XP BSOD's on startup. I have posted in a Windows forum, but they seem to be terrified that I've used the word "Ubuntu" or maybe I'm being plain impatient. Do you know of anywhere which specialises in dual-boot problems or something? Thanks again :)*

---

### Post by meierfra. on 2010-01-27
> Semi-related: After installing Ubuntu my Windows XP BSOD's on startup. I have posted in a Windows forum, but they seem to be terrified that I've used the word "Ubuntu" or maybe I'm being plain impatient. Do you know of anywhere which specialises in dual-boot problems or something? Thanks again
Start a new thread on the subject and I will have  look at it. To get started, follow these [instruction]("http://bootinfoscript.sourceforge.net") to run the Boot Info Script and post the RESULTS.txt in your new thread.

---

### Post by adam814 on 2010-01-27
Did you by any chance install using wubi?  I've heard of a lot of cases where kernel updates cause breakage in wubi installs.

---

### Post by Giltrap on 2010-01-28
> **meierfra. said:**
> Start a new thread on the subject and I will have  look at it. To get started, follow these [instruction]("http://bootinfoscript.sourceforge.net") to run the Boot Info Script and post the RESULTS.txt in your new thread.

I've started a new thread about the Blue Screens, and posted the RESULTS.txt at the bottom of it. [http://ubuntuforums.org/showthread.php?t=1392524](http://ubuntuforums.org/showthread.php?t=1392524)

> **adam814 said:**
> Did you by any chance install using wubi?  I've heard of a lot of cases where kernel updates cause breakage in wubi installs.

I didn't use Wubi for this installation. I used a GParted live CD, made about 20 GB of unformatted space and installed it in there.

Thanks for the quick replies :)

---

