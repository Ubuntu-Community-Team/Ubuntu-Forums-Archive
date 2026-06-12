---
title: "The blue screen of death + Main OS not working"
date: 2007-07-12
forum: Installation &amp; Upgrades
---

### Post by Jeremywilms on 2007-07-12
Well THANKGOD I downloaded the CD Live onto a disk. My main OS is  kinda messed up. I had Windows Vista. but....When I tried to install ubuntu(This may be the reason) It kinda just stopped loading. So I pressed the cancel button(Step 5) I think it may be because my HD partion is in two. But ubunut is'nt installed. So basicly when I try to run my main OS(Vista) I get the blue screen of death to fast to read, then it reboots. So basicly my question is. "Is there anyway I can fix My main OS(Vista) while runnig ubuntu(not installed)?)

---

### Post by Jeremywilms on 2007-07-12
kk well I cant accsess my HD, and I can't downlaod anything(as far as I'm conserned) and I can see any windows files, how could I.

1.Accsess my HD
2.Fix my main OS
3.View Microsoft Windows Files.

---

### Post by merlinus on 2007-07-12
Can you boot from the ubuntu live cd?  

-merlin

---

### Post by Jeremywilms on 2007-07-12
Yes, Thats what i'm doing right now.

---

### Post by ageilers on 2007-07-12
Keep pressing F8 while booting you should be able to select an option to turn off automatic reboot. there should be an option for last known good configuration.

---

### Post by merlinus on 2007-07-12
What is the output of:

```

sudo fdisk -l

```

-merlin

---

### Post by Jeremywilms on 2007-07-12
> **ageilers said:**
> Keep pressing F8 while booting you should be able to select an option to turn off automatic reboot. there should be an option for last known good configuration.

ookay, i'll give it a shot, Thanks

---

### Post by Jeremywilms on 2007-07-12
It did'nt work. I think its my OS(XP) thats messed up. What happend is I get about 3 seconds in to that sighn that displays Windows is loading. With the load bar at the bottom. Then I get this blue screen that pops up and then the computer reboots after really fast.

---

### Post by Jeremywilms on 2007-07-13
> a problem has been detcted and windows hs ben shudwn to revent damage to your computer.

PROCSS1_INITALIZATION_FAILED

If this is they first time yo hav seen this "Stop error screen" retart yourcomputer(Tried 20 times) If this screen apears again follow hes insructions:

-Check to make sure new hardware or software s nstalled coorectly(Ubuntu intller crahed on me. well not crashed but justtoed kinda thing.)

-If this pobem continues disable or remove any newlynstalled hardware or software. Disable BIOS memory option such as catching and shaowing. If you need youse safe mode to remove components, restart and boot in safe-mode

Thats what the error message says, it shows while windows is loading
P.S Don't ask question because I can't reply them until 4:00 Iav these Javas classes I have to get to, and sorry for the many spelling errors, this key board keeps mising keys.

---

### Post by Jeremywilms on 2007-07-13
Read Above^^
*bump*
Sorry if it looks like i'm being self-ish or somthing. Or even somwhat rude. I just don't have time on my hands to bring this in to the shop. I can't really develop much with vista, so I would really like it if someone could figure out this problem. Sorry XD.

---

### Post by Wiebelhaus on 2007-07-14
Sounds Like hardware issues , Two OS's Blowing up , Take it to a shop , they'll diagnose it for around 30 bucks and give you an definitive answer.


DO NOT take it to best buy or circuit city for the love of god take it to a real Computer Repair shop.

---

### Post by Jeremywilms on 2007-07-14
I can still launch my computer with ubuntu CD LIVE, is there anyway I can fix it like that.

---

### Post by iAlta on 2007-07-14
Isn't just that Ubuntu has overwritten the mbr?

---

### Post by Wiebelhaus on 2007-07-14
Search MS support documents on how to [repair the boot loader]("http://support.microsoft.com/kb/919529") , bcdedit.exe is really the only good change to vista , this might allow you to gain access to your main installation if not , your hdd failed , also was vista pooched before your exploration with ubuntu?

---

