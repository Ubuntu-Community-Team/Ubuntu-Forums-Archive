---
title: "Dual boot problem.."
date: 2008-02-05
forum: Installation &amp; Upgrades
---

### Post by jeb on 2008-02-05
Hm, sorry if this a bit vauge but. I decided to install Ubuntu on my other computer on a secondary hard drive (sata; simpler), and Windows worked fine after that..besides the fact it didn't realize Ubuntu existed , so I changed the boot order of the drives so that the secondary was the main boot drive (after setting it in the XP partition; on the other drive, was not tagged as boot in gparted so that it would load the GRUB Bootloader).
  
 GRUB Detected windows , and when I tried to boot into windows off of GRUB it went into system recovery (o_O??) . I did what it said..(dumb me, obviously.) Aaand, now, it gives "NTLDR is missing" no matter what boot order I have the drives in, or it goes to the gateway system recovery thing, and I can't access GRUB either. Should I boot off my liveCD and reinstall grub? I honestly have no idea what to do - I can't use the fixmbr thing on the Windows disk cause my computer (years old; although I have changed many parts in it including motherboards, processors..etc in the past few months) was an OEM system .. 

Thanks, 
             [INDENT]- Jeb[/INDENT]

---

### Post by Herman on 2008-02-05
:) Hello jeb, 
The web page in this link should help you for now, [How to fix: MYLDR is missing, press any key to restart]("http://tinyempire.com/notes/ntldrismissing.htm").
What did Windows get you to do? Can you remember?
I'm not sure what else to tell you because I'm not sure what's wrong.

Probably everything would have been okay if you used a couple of [map commands]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") to trick Windows into thinking it was in the first hard drive.

Re-installing GRUB won't help you. Maybe you can get out of your problem by editing boot.ini in Windows to tell it it's now in the second disk. That might work, I'm not sure. It might be worth a try. You should be able to get Windows to boot for you with a CD downloaded from that link I already gave you, then you could take a look at boot.ini and see if it looks okay or not.
Or maybe just try using the map commands in GRUB, that would be much easier then editing boot.ini.

Regards, Herman :)

---

### Post by jeb on 2008-02-05
Thanks for the link - I'm going to try it later.  Before the NTLDR problem started it automatically booted into system restore when I tried to boot off grub; I let it do it's thing and than the issue with NTLDR started o.o;

---

### Post by hyperair on 2008-02-05
You could actually just boot into Ubuntu and get the files, then dump it in the root of that drive.

---

