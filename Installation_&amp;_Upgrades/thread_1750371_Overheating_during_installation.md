---
title: "Overheating during installation"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by Strider11o7 on 2011-05-05
I'm using a Dell Studio 15 and recently burned a new 11.04 disk to try and replace my old Ubuntu partition which crashed permanently (it was my fault btw). Anyways, I've been using Windows 7 and recently I've had trouble with my computer overheating very easily, just watching a video with sound and it will crash after 10-15 minutes, so it's been seemingly impossible to install 11.04.

I've gotten it to the setup screen once before crashing, but that's longest it has ever lasted, and one time it went to a login screen to which I had to restart since I had no options available. I've tried using fans and keeping the room as breezy and cool as possible, and I've also considered sticking it in the fridge while it boots up, but that just seems like a desperate and dumb idea. Any suggestions?

---

### Post by Joe of loath on 2011-05-05
Open the bottom and clean the dust out of the heatsinks. Also, if you have any, replace the thermal compound between the CPU and heatsink, it may have gone off.

---

### Post by meanpt on 2011-05-05
> **Joe of loath said:**
> Open the bottom and clean the dust out of the heatsinks. Also, if you have any, replace the thermal compound between the CPU and heatsink, it may have gone off.

On a new HP tm2 tablet I experience the same and  some times the installation breaks due to thermal problems as they're being reported. I'm not sure if your ... well, "solution" is really meant to help. Lets hope someone else may come with a better idea, eg how to "calm down" the hunger for cpu during the installation. We are talking about  individual's big bucks investment, and not wishing to joke or jerk with it.

---

### Post by Joe of loath on 2011-05-05
My 'Solution' is the most permanent. The CPU load WILL be 100% most of the way through the installation, if your PC can't cope with that, something is wrong. A PC should be able to run at 100% CPU indefinitely, as that is the test for a stable overclock. You leave it running prime95 for a week, if it's still going at the end, your overclock is stable. Throttling the CPU is a stupid idea, since it's only a temporary solution to a potentially serious problem (CPUs aren't cheap to replace), and kills your performance anyway.

---

### Post by Strider11o7 on 2011-05-05
Thanks for the tips I'll try that this weekend.

---

### Post by meanpt on 2011-05-06
> **Joe of loath said:**
> My 'Solution' is the most permanent. The CPU load WILL be 100% most of the way through the installation, if your PC can't cope with that, something is wrong. A PC should be able to run at 100% CPU indefinitely, as that is the test for a stable overclock. You leave it running prime95 for a week, if it's still going at the end, your overclock is stable. Throttling the CPU is a stupid idea, since it's only a temporary solution to a potentially serious problem (CPUs aren't cheap to replace), and kills your performance anyway.


There is nothing wrong with my laptop, it just can't cope with those thermal loads as some desktops and portable workstations with improved cooling systems do. It doesn't make sense that an installation of ubuntu breaks due to exceeded  thermal limits, as the error is reported, and it means ubuntu don't and can't  recognize that those thermal limits exist.

---

### Post by Joe of loath on 2011-05-06
> **meanpt said:**
> There is nothing wrong with my laptop, it just can't cope with those thermal loads as some desktops and portable workstations with improved cooling systems. It doesn't make sense that an installation of ubuntu breaks due to exceeded  thermal limits, as the error is reported, and it means ubuntu don't and can't  recognize that those thermal limits exist.

If it's still overheating, something IS wrong. Talk to the manufacturer. Ubuntu shouldn't slow itself down if the PC gets too hot, that's the job of the BIOS to run the fans and the manufacturer to design a decent cooling system.

---

