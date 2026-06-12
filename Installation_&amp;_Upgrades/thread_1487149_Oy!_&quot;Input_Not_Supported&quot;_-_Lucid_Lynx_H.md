---
title: "Oy! &quot;Input Not Supported&quot; - Lucid Lynx Has Lassoed Me"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by gmhead on 2010-05-18
OK - I've contemplated trying Ubuntu and d/l'ed the 10.04 LTS iso - no joy.  2 different machines, both give the same message "Input Not Supported".
:confused:
I am a rank (no, not stinky) beginner.

Focusing on machine #1:
ABIT AV8 MoBo, 1 Gb RAM, BIOS upgraded, AMD Athlon64 FX939
Visiontek AGP graphics card - Radeon 9600 256M DDR
 (is this the culprit?)

Clean install using the text-based installed - all seemed fine until the Moment of Truth (AKA reboot) - "Input Not Supported" appears in a grey box with red letters, flashing on and off.

Started the "LiveCD" - was able to run 10.04 off that by 1st selecting the language, then pressing F6 and checking "nomodeset".  Boots fine.:KS

I suppose there's a fix somewhere on this forum; I've seen this "nomodeset" situation before.  Question:  if video cards are so hinky, why isn't "nomodeset" the default (not that I really understand what "nomodeset" means...)?

So closer than yesterday, closer than the day before that, and the day before that.:-k

---

### Post by gordintoronto on 2010-05-18
Most monitors have no problem, and Linux accurately selects the appropriate resolution and refresh rate. If nomodeset was the default, users would have to specify it -- and 25% of them would be completely baffled.

What monitor do you have? What are its nominal settings?

Do you get a Grub menu?

---

### Post by gmhead on 2010-05-18
I doubt it was the monitor, but who knows?  I don't have clue 1 as to what "nomodeset" is all about - I figure I'll learn eventually.  

I did solve it and yes, after I figured out how to invoke GRUB, I now have it up and running ('cept I installed the 32-bit version and wanted to install the 64-bit OS).

I posted it as a solved thread here:  [http://ubuntuforums.org/showthread.php?t=1487253&highlight=Video+issues+installation](http://ubuntuforums.org/showthread.php?t=1487253&highlight=Video+issues+installation)

Sometimes I need to have things "ducks and bunnies" in order to make it understandable to me.  I know that by figuring it out I have learned it.

Thanks for the response.

---

