---
title: "Gutsy not recognizing Vista install"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by audrey_osu on 2007-10-20
I hope this hasn't been covered... I couldn't find it...

I am very new to Ubuntu and I haven't tried Linux in years...  I want to dual boot gutsy with vista (I think I have the partitioning figured out) but when I get past that it doesn't recognize my vista install in order to migrate my settings into Ubuntu... 

I am sure I could just give up on this and set up Ubuntu the way I want... but this feature is pretty appealing and I'd rather just hit the ground running...

Can anyone help?

Thanks!

Audrey

---

### Post by pakfm on 2007-10-20
I have the same problem - but for Windows XP. I did a guided resize of the partition, but the next window did not detect any installed operating system, so I canceled the installation fearing that I would not be able to boot back into XP after installing.

After rebooting, chkdsk ran and XP booted fine, and saw a new unallocated partition in disk management. Going back into the Live CD, XP is still not detected by the migration assistant. I can mount the drive and explore it fine however.

---

### Post by thekid8907 on 2007-10-20
Grub is not recognizing Vista on my system either..It will load to the boot screen but they are all options for ubuntu and none for vista..??

i have been trying to get help with this all day but nobody seems to want to help me around here

---

### Post by thekid8907 on 2007-10-20
Help Please!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!@!!!!!!!!

---

### Post by audrey_osu on 2007-10-20
> **thekid8907 said:**
> 
i have been trying to get help with this all day but nobody seems to want to help me around here

Yeah, I even got on IRC - I was ignored except for one guy that told me Vista won't dual boot with linux.  The only other person responded to say that guy was wrong... obviously...

This feature is one of the big selling points of switching for me... I'll probably just wait a few more years if its not an easy fix...

---

### Post by kamaboko on 2007-10-20
me too.  i see it on grub, but when i select it vista just hangs during the load phase.  the flash bar just keeps cycling.  i just kissed vista goodbye.  if i have to i'll reinstall it if i can't get gutsy to work.

---

### Post by pakfm on 2007-10-20
Just tried with the 7.04 Live CD, the migration window properly detects all of my accounts from XP, so something must have changed between releases.

---

### Post by tuscani20001 on 2007-10-20
I think what you can do is boot with your vista cd, then choose repair and using command prompt re-edit the bcdedit.exe

That did the job for me. though I cannot access ubuntu because it stalls when loading hardware drivers. Vista works fine though.

---

### Post by LDRoamer on 2007-10-20
You should do a search of the forums for dual booting vista. There is a bunch of information that has been posted that is likely useful to you.

---

### Post by audrey_osu on 2007-10-20
Dual booting isn't my problem.... its migrating my vista settings to Ubuntu...

---

