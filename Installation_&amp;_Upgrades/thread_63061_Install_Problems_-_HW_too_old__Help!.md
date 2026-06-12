---
title: "Install Problems - H/W too old?  Help!"
date: 2005-09-06
forum: Installation &amp; Upgrades
---

### Post by winburne on 2005-09-06
Hello:

I have tried to install 5.04 at least 5+ times this weekend – without success.  …went through 2 mobo/CPU/RAM setups, 3 HDs, 3 ISO burns after checking md5 on 2 separate D/Ls.  I’m going crazy!  Found one bad HD and one bad RAM module – that was real fun.  Of course, each time I replaced the bad component, I got better results, but that meant further along the install process before freezing!  Agghhhh!

Calm down, Rob.  OK… That’s better.  Now, I think that I have 2 systems that I can build that have good (working) hardware.  But I’m not sure if either system is adequate - evidentially not.  Here’s what I have:

Currently trying:                     Alternate (have tried):
  Soyo K7VIA                             Abit KR7A
  Athlon 750 GHz                       Athlon XP 2000
  3x256 MB PC133                    1x256 MB PC266
  Gainward TNT2                       common
  3Com 3D905C-TX                   common
  3.2GB WD Caviar (33MB/s)     common
  newer 48-24-48 CD-RW         common
  on-board sound                     some old SB card

I am planning on adding a big HD and using this machine mainly for a file server for home network, but would like to also play around and learn something new (want comforting GUI).

Q1 – Can you see anything wrong with my hardware?  HD too small?
Q2 – Which system would you build: Soyo (more RAM) or Abit (faster CPU)?
Q3 – Any BIOS settings needed/beneficial?  ACPI disable?  PNP OS?  Other?

Here is some more info about my many installation failures (from memory):
-Installation detects and configures HW and network connection fine.
-All blue screens run fine although very slow.
-Lots of errors when “selecting previously deselected… / unpacking” 
-unpacking/extracting components was very, very, very slow (4-6 hours – fell asleep).
-Last install attempt froze after setting the time zone.
-Live CD seems to run OK.
-Tried server install – seemed OK, but had problems adding GUI & other components with “apt-get install…”.  Many error messages when adding components.  

Anyway, thanks for reading this far, wow.  I really appreciate any help you can offer.

-Rob

---

### Post by skoal on 2005-09-06
Use the Athlon XP 2000 (fastest proc), the KR7A, and anything else.    Then, only use 1 stick of 256 MB Ram (the PC266).  If you choose the other CPU/mobo route, choose any 1 stick from the 3.  Run a memtest (with a live CD) on that stick.  If it checks out OK, that's more than enough memory to complete the install.

I've completed an Ubuntu install on a *far* inferior rig than what you got there, and it only took me < 10 minutes for the I/O transfer (on a 16x CD-Rom and a PIO Mode 2 hdd).  Either system is more than adequate.  Make sure you run BIOS first and set everything back to default settings if you're still having problems.  It looks like those two boards are overclockable, and depending on where you got it from, you may need to tune it down a bit for stability.

\\//_

---

### Post by az on 2005-09-06
"Q3 – Any BIOS settings needed/beneficial?  ACPI disable?  PNP OS?  Other?"
ACPI works better if your Mobo has it.  You can even try acpi=force if you know that your board has it, but the kernel chickens out. 

PNP OS = NO


"-All blue screens run fine although very slow."

What is slow.  I can run through the first steps and get to the last question of the partitioner (do you want to do this, yes or no?)  in about five minutes.  This is on a pentium one, 166 MHz machine.  I can do it in three minutes on a faster machine.

"-Lots of errors when “selecting previously deselected… / unpacking” 
Errors of messages?

"-unpacking/extracting components was very, very, very slow (4-6 hours – fell asleep)."

Takes two or three on the above pentium one.


"-Tried server install – seemed OK, but had problems adding GUI & other components with “apt-get install…”.  Many error messages when adding components.  "

What errors?  Do you have a corrupt cd?

---

### Post by winburne on 2005-09-07
"Q3 – Any BIOS settings needed/beneficial?  ACPI disable?  PNP OS?  Other?"
ACPI works better if your Mobo has it.  You can even try acpi=force if you know that your board has it, but the kernel chickens out. 

PNP OS = NO

++ Thanks.

"-All blue screens run fine although very slow."

What is slow.  I can run through the first steps and get to the last question of the partitioner (do you want to do this, yes or no?)  in about five minutes.  This is on a pentium one, 166 MHz machine.  I can do it in three minutes on a faster machine.

++ I can do that in about ~1min.  It's the copying "main" files (??) to the HD (slow)and then unpacking/extracting components after reboot that really slows to a crawl/stop.

"-Lots of errors when “selecting previously deselected… / unpacking” 
Errors of messages?

++ I'll try again tonight and document everything better...

"-unpacking/extracting components was very, very, very slow (4-6 hours – fell asleep)."

Takes two or three on the above pentium one.

++ Something's wrong here, I'm taking much longer on a faster machine.


"-Tried server install – seemed OK, but had problems adding GUI & other components with “apt-get install…”.  Many error messages when adding components.  "

What errors?  

++ I'll document on my next try.

Do you have a corrupt cd?
++ I don't think so, I'd have to have 3 bad (slow burned) CDs from 2 confirmed D/Ls.

++ Thanks

---

### Post by winburne on 2005-09-08
On my latest attempt:

Changes:
- HD to newer 20GB (working in and stolen from kids PC)
- new HD cables
- new burned CD (burned at 8x w/ different media)

Things to know:
- It took a couple of times to boot from the CD ("BOOT from CD failures")
- burned CD on NEC 3520 (DVD-RW) w/ NERO 6.x ---- 8x is slowest setting
- Install ran fine until "installing ubuntu base system", then somewhere in there, I got a "boot strap" error.  
- Went back and tried to re-partition, no luck.
- forced CD out and replaced with another to install system, no luck

Could it be that I'm using a DVD burner to burn my CDs?

Thanks for reading, I really appreciate the help.

-Rob

---

