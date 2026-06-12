---
title: "Karmic, slow boot, &gt; 2 min"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by musicman99 on 2009-12-26
On my 1 Ghz Athlon, I'm getting weird with the start up time... Vanilla installation, from yesterday. all upgrades done.
after GRUB (Grub2) no movement for 1 min ... see bootchart attached.
Ubuntu/Linux newbie... no idea what is happening. 
Any idea?

thankx

---

### Post by SteveDee on 2009-12-26
I can't see the detail on your chart. Try checking your event log via menu System > Administrator > Log File Viewer > messages...

...or open the /var/log/messages file in a text editor.

---

### Post by musicman99 on 2009-12-27
see message log showing the logs beginning with a restart.
After Grub2 there is no movement ...
bootchart is showing the same. 65 seconds nothing, no activity, obviously no kernel activity :-(

---

### Post by SteveDee on 2009-12-28
I'm sorry I don't know what the problem is. But here are my suggestions (at the very least this will bump your thread!).

I wonder if its a Grub problem or an issue with your hardware (e.g. a HDD problem or a bad ref to the HDD in Grub).
1. Take a look at menu System > Administration > Disk Utility > More Information   {anything odd there?}
2. Boot system from a Linux LiveCD or memory stick (e.g. Ubuntu, Puppy Linux or other suitable distro)  {does it still have this inactive period during boot?}
3. Consider re-installing Grub {info at several sites including: http://members.iinet.net/~herman546/p20.html}

---

### Post by t.rei on 2009-12-28
The one thing that REALLY slows down any boot on my machine is grub2 loading. From poweron to grub menu thats about 30 seconds. Loading to login-manager then is a matter of about another 20-30 seconds. Then desktop loading begins... and THAT is about a minute untill workable.
I'm not really shure why this is. I checked whats loaded and theres really nothing noteworthy there (kde+kwin, altho I would prefer compiz as its more feature-complete, I chose kwin for 'integrety' reasons). 
So - I don't have an answer for you, but I'll shurely keep an eye on this thread. ;)

---

