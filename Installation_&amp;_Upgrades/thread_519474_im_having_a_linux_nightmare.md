---
title: "im having a linux nightmare"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by sent17inel on 2007-08-07
my brothers friend came over and saw my ubuntu computer with cpmpiz fusion and a couple days later he brings his tower over saying he wants ubuntu on his computer. I say no prob since I have the live cd it should be a piece of cake. so I pop in the live cd and nada. nothing happens. he has a gateway with a pentium three and 512mb of ram. his cd drive looks old as hell... I went into the bios and changed the boot options so that it would boot from the cd and still I got nothing. it had windows 98 on it till I took out his hard drive and put it in mine as a slave. I installed ubuntu on it then took it out an popped it back in his computer and powered it on and then it said no operating system found... or something... so then I'm like damn todays not my day. so I put his computer off to the side and try to enjoy the rest of my evening on my computer. I turn on my computer an get hit with grub error 21. so I go and reinstall grub. got my computer back an working now but I'm still baffeled as to qhy ubuntu won't work  and the gateway. any ideas?

---

### Post by aquavitae on 2007-08-07
Your computer probably had the error because you'd changed hardware (i.e. put your hdd in his computer).  As for your friend's pc... I'm not surprised yours didn't work is his, especially with compiz!  Ancient computer like that, I'd suggest using xbuntu rather than ubuntu.  Anyway, have you checked if his cd drive actually works?  Try it in your pc, or try another one in his - if its that old that's the most likely problem.

---

### Post by Wim Sturkenboom on 2007-08-07
When you installed on the second HD, you overwrote your MBR, not the one on your friends HD.
Grub on your machine is (was) now looking for something on the second HD so it does not work. There is nothing in the MBR on your friend's HD, so it does not want to boot (no OS found message).
Stick his HD in your PC as the only disk and fix GRUB (or re-install).

@aquaviate
Not booting has nothing to do with Compiz. Further (in my opinion) it highly depends on the clockspeed if Ubuntu will work nicely or not.

---

### Post by aquavitae on 2007-08-07
> **Wim Sturkenboom said:**
> 
Not booting has nothing to do with Compiz. Further (in my opinion) it highly depends on the clockspeed if Ubuntu will work nicely or not.I know compiz has nothing to do with booting, but it might have something to do with x not starting, which a newbie might think means not booting.  True, clockspeed makes a huge difference, but chances are on an old pc, it won't be great.  Anyway cpu does also make quite a difference.

---

### Post by Wim Sturkenboom on 2007-08-07
The message was "no os found' :)

PS Edited my previous post slightly to make that more clear.

---

### Post by Lord Illidan on 2007-08-07
Old computer like that, better off with Zenwalk Linux.

---

### Post by sent17inel on 2007-08-07
Dude... i knew putting his hard drve as a slave messed up my mbr. I already fixed grub before i made my first post. I just want to know if you have any idea why the linux cd wont boot into live cd mode. It just doesnt make any sense to me. He has enough ram. his processor meets the requirments. Does anyone have any ideas why it might not be working?

---

### Post by sent17inel on 2007-08-07
Solved it... it must have been the bad cd drive because i swapped it out for an old cd rw i had in the attic and it worked....

---

### Post by Wim Sturkenboom on 2007-08-07
> **sent17inel said:**
> Dude... i knew putting his hard drve as a slave messed up my mbr. I already fixed grub before i made my first post.I know that you fixed your grub and I also know that you were not able to fix it in your friends PC before you made your first post (so you obviously did not know what was wrong there).

> **sent17inel said:**
> I just want to know if you have any idea why the linux cd wont boot into live cd mode.That was not your original question; the below was:
> **sent17inel said:**
> ... but I'm still baffeled as to qhy ubuntu won't work  and the gateway. any ideas?


But OK, congrats on fixing the HW

---

