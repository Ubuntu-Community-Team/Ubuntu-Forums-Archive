---
title: "upgraded to 15.04 - boots to a frozen screen"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by jgw on 2015-04-28
I upgraded to 15.04 and, now, it kinda boots to a frozen screen.  The screen itself is a mess.  The launchpad shows a line of multi-colored boxes.  The top is a bunch of multi-colored lines.  my mouse moves but nothing else is accessable.  My thought is to download the new dvd and simply re-install but thought I would put this up and see if anybody had any thoughts.  I have also tried just about every key combination in an effort to see if anything would change - nothing changed.  It also takes a long time to boot up and there is an error that goes like; "acpi pcc probe failed.  starting version 219"  (I have no idea if this has anything to do with anything)

Thank you.................

---

### Post by kc1di on 2015-04-28
Hi jgw,

do you by any chance have a Nvidia video card?  if so you'll need to boot with the nomodeset or nouveau.noaccel=1 boot parameter the first time until you can install the proper driver. 

ATI/AMD cards also may have similar problems.

---

### Post by jgw on 2015-04-29
Thank you for the reply.  

I figured out how to do the nomodeset and the nouveau.noaccel=1.  It seemed to almost work but the machine just kept on doing stuff and, eventually, ended up with a black screen.  Then I went back in to the grub edit screen and found that "nomodeset" had reverted to "quiet splash".  I then went back in and replaced "quiet splash" with "nouveau.noaccel=1".  This time it asked me for a password.  After I entered that I think it put up another workspace (which I cannot seem to get rid of).  As I continued to see what works the screen would go blank/black and then the screen would come back and ask for my password again.  Its very strange.  Oh, the unity launcher is still full of semi-blank boxes too.  

I think my wisest move, at this time, is to revert back to 14.??

---

### Post by kc1di on 2015-04-29
You may be right on 14.  I've seen several post about Nvidia cards not working right on 15.04. Good Luck

---

