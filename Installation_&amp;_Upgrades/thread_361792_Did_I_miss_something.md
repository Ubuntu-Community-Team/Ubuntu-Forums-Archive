---
title: "Did I miss something?"
date: 2007-02-14
forum: Installation &amp; Upgrades
---

### Post by KatieCook on 2007-02-14
<some history>I have been trying to figure out which linux distro is going to work with my old machine.. *pent 3, 256 RAM, 10 Gig hd.*  Just when I think I have it.. The same thing always happens.. It freezes after opening up a couple of programs.. I am starting to think it is my memory for this machine.  


1st question: 
  What did I miss?  When I "installed" ubuntu 5.10 where is the desktop?? Do I have to install something else or use a magic command to see it?  

2nd question: 
 Is there a way I can check my memory to see if that is what is causing the trouble?

3rd question:
 Does it sound to you like that could be the problem?

Thanks so much for any help I can get. :)

---

### Post by Kateikyoushi on 2007-02-14
2. After you boot from the ubuntu discs you have an option to run a memory check.

1. What do you see after installation, still terminal ? What do you mean with where is the desktop ?

---

### Post by Zimmer on 2007-02-14
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

A link full of interesting options for Low Memory and older machines.

I tried loading various Linux small Distros on an old machine without success and mostly it was graphics that was the limiting factor running any sort of 'desktop' .
What graphics card do you have? How much memory does it have?
[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCards)

As for checking your memory, there are various Live CD's that come with a memory check program.. and maybe you can run one from your BIOS (not sure about that) . I will try and find one for you and report back !
EDIT memtest is on the Alternate DAPPER Install CD

---

### Post by KatieCook on 2007-02-14
> **Kateikyoushi said:**
> 2. After you boot from the ubuntu discs you have an option to run a memory check.


 So I should put the disk back in and check it from there?



1. What do you see after installation, still terminal ? What do you mean with where is the desktop ?

When I boot up i get this...  katie@ubuntumom:~$  _

---

### Post by IgnorantGuru on 2007-02-14
In my experience a machine with those specs should run the current version of Ubuntu 6.10 Edgy fine.  But I would suggest using the Alternate Install CD rather than the live CD.

If your desktop doesn't come up, perhaps the X server isn't starting properly.  Type startx and see what it says.  A newer version might support your hardware better.

To test memory, the alternate install CD has a memory tester on the initial menu, or you can download SystemRescueCD iso, burn the image to CD, boot it, and type memtest at the Boot: prompt.   [www.sysresccd.org](www.sysresccd.org)

Could be memory.  Could also be a funky power supply, or a video card issue.  For now stick with the open-source (default) video drivers that Ubuntu installs.

---

### Post by KatieCook on 2007-02-14
> **IgnorantGuru said:**
>   Type startx and see what it says.  A newer version might support your hardware better.


I typed in startx and got...... -bash: startx: command not found

I had 6.06 loaded on it and it looked great and loaded very easy, but again it would freeze up anytime I started to look around. So I thought I needed an eariler one.. I would love to see the desk top of 6.06 again on it trust me.. LOL  But it keeps freezing up so I can only do just that .. look at it.  
I have been using it as a live CD on my newer computer that I am writing this on and I LOVE IT!!!

---

### Post by IgnorantGuru on 2007-02-14
> bash: startx: command not found

Odd.  I'm not familiar with that version of Ubuntu.   Maybe "sudo startx" would do it.

I don't think the machine freezing up is due to your older hardware, so I would suggest sticking with a more current version - 6.06 or 6.10.

Are you sure the hardware is healthy?  Were you running another OS on it okay prior to Ubuntu?  I would definitely test the memory.  Hard to narrow down those freezes, but if it does it with multiple versions it sounds like it might be hardware.  Flaky powersupply, memory, video card, overheating, etc.

Also see if you can make it freeze up predictably - when you run a particular program or function.  If it's completely random that also indicates it may be hardware (but not definitely).

---

### Post by KatieCook on 2007-02-14
Ignorant.. 

  It it strange.. when I put mepis on this computer, it froze when I right clicked the mouse.. but ubuntu 6.06 responded for much much longer.  but sometimes it will do fine for a short time and just when I get going it freezes up.. I mean FROZEN ~ STUCK ~ TURN ME OFF!!! 

  It had Windows ME on it before, and the only reason I wanted to change it was ME was conflicting with everything.. printer and camera not playing nice, then scanner and mp3 player conflicting so I got tired of removing something to use another thing. I have tried and tried to study up on the dual booting but my brain will just not get it, so I thought it would be best to just wipe it clean and load another OS.. Hummmm maybe I should have tried the study route one last time. LOL 

 I am testing the memory now.. wow it sure takes a long time.. at this rate it will be done in a couple of days.

---

### Post by KatieCook on 2007-02-15
Nope, sudo startx did not work either .. still can not see desk top :confused:

---

### Post by Kateikyoushi on 2007-02-15
> **KatieCook said:**
> So I should put the disk back in and check it from there?



1. What do you see after installation, still terminal ? What do you mean with where is the desktop ?

When I boot up i get this...  katie@ubuntumom:~$  _

Yes you should put the disc in the drive reboot load the disc and at the menu select memory check.

In my opinion installation did not work out as it should might be a reason of bad memory.
Try the memory test.

---

### Post by KatieCook on 2007-02-15
Thanks, it started and still had not finished 3 hours later and so I stopped it, but I will start it again before I go to bed, hopefully it will be done before I wake up LOL

---

### Post by KatieCook on 2007-02-15
Thanks for your help, I could not get past the blinking curser and before I started curing, I went back to 6.06 and so far so good, no freezing, but i still went ahead and ordered new ram.. :)

---

