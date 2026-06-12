---
title: "Cannot start Ubuntu 5.04 live amd64"
date: 2005-05-27
forum: Installation &amp; Upgrades
---

### Post by rigg on 2005-05-27
Hi, totally new to Linux I tried to start my computer with Ubuntu 5.04 live amd64.

When it seems that the boot up is in the final part, it stops and says "I cannot start the x-server....."

From the error message I can see this (totally non-understandable for me):

[COLOR=Indigo]Skipping "/usr/x11R6/lib/modules/extensions/lib GLcore.a:m_debug_clip.o"
no symbols found
Skipping "/usr/x11R6/lib/modules/extensions/lib GLcore.a:m_debug_norm.o"
no symbols found
Skipping "/usr/x11R6/lib/modules/extensions/lib GLcore.a:m_debug_xform.o"
no symbols found

(EE) No devices detected

Fatal server error: no screens found[/COLOR]

My computer is 

Intel P4 650 3.4GHz HT / 64 bit
1536 MB DDR
ATI Radeon XT
SB Audigy 2 ZS Platinum

Can someone help me, or do I have to give some more information?

/rigg

---

### Post by rtz654 on 2005-05-27
Do you have a 32bit version of the live cd? maybe you should give that one a try!!

Unfortunately it might be that your brand-new equipment is not yet fully functional under ubuntu (or any other linux). If you wuold like to give it a "easy" start get this old 500MHz Pentium back from the cellar and make your first steps there  ;-)

---

### Post by rigg on 2005-05-27
[QUOTE=rtz654]If you wuold like to give it a "easy" start get this old 500MHz Pentium back from the cellar and make your first steps there  ;-)[/QUOTE]

Do I know you? I really have an old P 500Mz in the cellar (as a webserv (wk3 serv), thats the next project)

;)

/rigg

---

### Post by rigg on 2005-05-27
[QUOTE=rtz654]Do you have a 32bit version of the live cd? maybe you should give that one a try!!
[/QUOTE]

tried the i386 version, same error... :(

tried it on my p3 500, started up fine exept that the mouse was dead (maybe my cordless logitec)

/rigg

---

### Post by rigg on 2005-05-27
Found the error: graphic card, used advanced boot /w vesa graphics...

Now I have other problems, shall do searching before posting ;)

/rigg

---

### Post by yay4furryanimals on 2006-04-25
Same here, I fixed mine by booting with live-export, then specifying vesa

---

