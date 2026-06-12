---
title: "Jaunty runs flawlessy; subsequent upgrades all freeze"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by techiewannabe on 2011-09-03
I've been using Jaunty for a couple of years. It has worked flawlessly for me. Whenever I have tried to upgrade to a newer version of Ubuntu, my system randomly freezes. It cannot be restored without rebooting the computer. (I have tried 9.10 and 10.04)

Currently, I have 10.04 on a separate partition of the same computer that is using Jaunty. Without fail, it will freeze up and require a reboot. Sometimes it will go for 20 minutes; sometimes for an hour and a half. I have searched the discussion groups and have not been able to find a solution to the problem. 

I am running a Compaq Presario laptop R3000 with 1.1 gb of memory. Platform is i686; CPU is an Intel Pentium 4 with 3.00 GHz. Chipset is ATi Radeon 9100 IGP / FSB 200: MHz.

Even though I've been using Ubuntu for quite some time, I still consider myself a newbie. I do not have a good understanding of the command line.

I would appreciate any help you can offer.

Thanks.

---

### Post by 2F4U on 2011-09-04
1. Do you see error messages in the system log when it freezes?
2. Is the laptop getting hotter under 10.04 than under 9.10?
3. Did you run a memtest (available on most liveCD's) in order to test the RAM?

---

### Post by coffeecat on 2011-09-04
Since you get freezes in 10.04, but not in 9.10 a hardware fault seems unlikely, but still possible. That's the trouble with random freezes. If you don't get them, you may be just having a run of good luck. That being said, I would guess there is an obscure bug specific to your hardware and one or more of the drivers in the kernel used in 10.04. Each newer version of Ubuntu uses a newer version of the kernel. You don't say whether you have tried something newer than 10.04, so I would suggest you do if you haven't already.

Download the ISO for 11.04/Natty and try running that live. Ignore all the moaning and groaning you may have seen about Natty in the forum - that's mostly knee-jerk dislike of the Unity interface. I have found Natty to be very stable on five different machines. You may be unlucky and find that it does not suit your machine but it is definitely worth giving a try because 9.10 is past end-of-life and you won't be getting any more updates for it.

---

### Post by techiewannabe on 2011-09-04
Thanks 2F4U  and Coffecat for your suggestions.

To clarify, I am currently running 9.04. It was when I went to 9.10 and above that I had problems. 

The memtest was fine. I'm not sure if my system is running hotter under the newer versions. How do I test for that? I am not sure how to search for errors in the system log. I know how to get to the system log, but don't know what specific script to look for. 

I have not tried 11.04/Natty because of some the negative hype that I had read about it. Perhaps it is time I give it a try.

Thanks for your comments. I look forward to any other suggestions that people want to offer.

---

### Post by techiewannabe on 2011-09-04
Well....I downloaded and installed on my hard drive Natty/11.04. I'm afraid that I continue to have the same problem. It looked like it was going to be a great OS, then it crashed!

Ideas anyone?

---

### Post by owise1 on 2011-09-04
have a read of the system logs -via log file viewer and see if there are any error messages  - might guide you to a solution

---

### Post by techiewannabe on 2011-09-04
owise1:
Thanks for your note. Can you guide me a bit as to what, specifically, I should look for in the logs -via log file?
Thanks.

---

### Post by owise1 on 2011-09-06
Hard to say what to look for but have a read of the logs for 

Xorg - I had a problem with a random freeze with a screensaver - got this message. [413285.248] (EE) intel(0): Detected a hung GPU, disabling acceleration. 

Also look at kern.log  syslog

These are in sort of plain english but you will have to read through to look for clues

---

### Post by mörgæs on 2011-09-07
Rather than installing Ubuntu 11.04 I would recommend Xubuntu 11.04, not only because it is fast on older machines, but because it is stable, unlike Ubuntu (as you have witnessed). 

This is of course not a complete guarantee, but a step worth trying.

---

### Post by techiewannabe on 2011-09-16
mörgæs:
Thanks for your note. I'm sorry that it has taken me this long to respond. Honestly, I had given up on this problem (and this thread....) I haven't checked it for a while.
I'll give you suggestions a try.
Thanks.
Techiewannabe.

---

