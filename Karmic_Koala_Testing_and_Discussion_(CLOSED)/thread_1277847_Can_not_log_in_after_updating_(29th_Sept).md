---
title: "Can not log in after updating (29th Sept)"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by victor9098 on 2009-09-28
I just got a few updates, restarted and after selecting my name and inputting password, the ubuntu screen comes up again and the system freezes. I have turned off and repeated several times now but still no luck.

Any thoughts?

---

### Post by lsmobrian on 2009-09-28
I got that too.  Does xsplash freeze?   When I view top in tty xplash is at 100%

I just kill that process and switch back to gui and I'm logged in

---

### Post by NormanFLinux on 2009-09-28
You may have to login via the console and then apply more updates if available.

---

### Post by victor9098 on 2009-09-28
You will have to explain to me how to do those actions!

I have tried logging by selecting 'Gnome Safe', but then nothing else loads in UNR, so I 'alt-F2', run synaptic, try to get updates but it does not say there is any.

---

### Post by lsmobrian on 2009-09-28
When its frozen press ctrl+alt+f1, this will give you a login prompt.  

Once youre logged in, use the 'top' command to see your processes.
likely, splash will be at 99%/100%, as is mine when I boot
look for the PID for xsplash, press ctrl+c to get out of top

then enter 'sudo kill -9 <XPSLASHES_PID>' (for me it was:  sudo kill -9 1702)
type exit to logout of tty1, you can then press ctrl+alt+f7 to get back to your gui and you should be at your desktop

---

### Post by victor9098 on 2009-09-28
> **lsmobrian said:**
> When its frozen press ctrl+alt+f1, this will give you a login prompt.  

Once youre logged in, use the 'top' command to see your processes.
likely, splash will be at 99%/100%, as is mine when I boot
look for the PID for xsplash, press ctrl+c to get out of top

then enter 'sudo kill -9 <XPSLASHES_PID>' (for me it was:  sudo kill -9 1702)
type exit to logout of tty1, you can then press ctrl+alt+f7 to get back to your gui and you should be at your desktop

THANK YOU! That got me back into my desktop, there was a crash report waiting for me regarding metacity (I presume unrelated) but not enough information for apport to make a report.

Will keep doing the above for the time being and hope that a update comes along soon to fix this.

Thanks again!

---

### Post by moebigsley on 2009-09-29
I am getting the same behavior as the original poster.
 
xsplash seems to hang and is consuming 99% processor.
 
This is occuring on a Dell mini 9 laptop with the karmic netbook remix. 
 
Is there a workaround or are we awaiting a fix?  Killing the process delivers the dektop, but all the panel applets are missing or bomb out.
 
- Moe

---

### Post by dimeotane on 2009-09-29
Similar problems happening here on a Toshiba NB200 netbook after last Ubuntu Netbook Remix update.  Worst update ever. Dumps to terminal login only. start gdm gives no keyboard or mouse.  System seems totally borked.  Trying recovery mode with networking to see if there's a new update that will solve this.

---

### Post by Joey French on 2009-09-30
Having this problem on Asus EeePC using UNR as well. xsplash hung at 99-100%. The solution outlined here works in the meantime...

---

### Post by xfalcox on 2009-09-30
Same thing here on eeepc 1000ha, most time it freeze. sometimes i got desktop without panels...

---

