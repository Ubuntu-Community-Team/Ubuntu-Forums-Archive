---
title: "Screen brightness set to zero at each bootup of 13.10-64 on a HP Pavilion dv4 Noteboo"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by Hakunka-Matata on 2013-12-21
New complete installation of 13.10-64 Desktop release on a HP Pavilion dv4 Notebook PC (WA684UA#ABA).  During boot, the purple Ubuntu screen shows for a moment, then goes black.  Machine boots up correctly, but the screen brightness must be turned up (alt-F8) before anything can be seen.  Once brightened, it runs fine until the next boot cycle.  Same scenario then repeats.  No additional drivers being used.

How to fix??

Thanks,

After searching around I may have found a fix for this:
 
[https://bugs.launchpad.net/ubuntu/+source/upower/+bug/968532](https://bugs.launchpad.net/ubuntu/+source/upower/+bug/968532)

Post #2: says;  [COLOR=#333333][FONT=Ubuntu Mono]I found this workaround (from [/FONT][/COLOR][bug #35223]("https://bugs.launchpad.net/bugs/35223")[COLOR=#333333][FONT=Ubuntu Mono], comment #51):[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]"[...] If I put[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]echo 2 > /sys/class/backlight/acpi_video0/brightness[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]in /etc/rc.local (before exit 0) it seems to work."[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu Mono]Indeed it works; I just changed 2 to 1, as 1 gives a low but acceptable brightness level on this lapto[/FONT][/COLOR]

After testing it I will mark solved if it works.

--------------------0---------------------------

I have tested and the results are good.

Yes, that does work for me, and of course it "sticks", since it is a change to etc/rc.local.  
echo 2 I've changed to echo 20, which sets brightness to 100% it appears, what kind of number base is that????????

marking this solved.

---

### Post by raja.genupula on 2013-12-21
have you tried any of these commands ?

[http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265](http://askubuntu.com/questions/149054/how-to-change-lcd-brightness-from-command-line-or-via-script/149265#149265)

---

### Post by Hakunka-Matata on 2013-12-22
Thank you raja, as you will notice in my original post (edited), it's fixed.

---

