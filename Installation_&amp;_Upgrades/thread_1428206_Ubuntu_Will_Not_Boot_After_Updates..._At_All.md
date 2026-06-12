---
title: "Ubuntu Will Not Boot After Updates... At All"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by Michael Kaiser on 2010-03-12
After running and installing updates (kernel 2.6.31-20) I performed the customary "reboot to complete installation". Upon re-boot I was greeted by the splash screen, then the load screen. The working/loading icon just spins indefinitely and Ubuntu won't load.

I posted this in another persons (with, apparently, the same type of problem) thread, and was recommended to try early versions of the kernel. NONE will boot.

Can anyone help me, please?

I don't know what I could possibly have done to cause this, and it seems that at least a couple other folks are having the same issue.

---

### Post by Michael Kaiser on 2010-03-12
Can anyone help?

---

### Post by Michael Kaiser on 2010-03-12
Anyone at all?

---

### Post by Michael Kaiser on 2010-03-13
Still seeking help.

---

### Post by souleke on 2010-03-13
if you can't start a early version then try a live cd and recover the system

try to find out more info on what whent wrong after/while your updating

---

### Post by bcbc on 2010-03-14
Any luck yet? Try checking this out: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:minix)

It's a long shot, but since it just happened out of the blue and affected all your kernels, it may be something like this (file system related bug).

edit: I just realised you already posted the bootinfoscript result. It would usually show 'ambivalent result' as the file system if the above bug affected you - so it's probably not going to help. Oh well...

---

### Post by oldfred on 2010-03-14
It sounds like you can boot grub but not Ubuntu hangs up somewhere. 

Have your used the recovery mode or manually edited the boot mode to remove the quiet & splash entries so you can see where it stops. That may help in figuring out where the problem is.

---

### Post by yakitori3 on 2010-04-23
same problem...will not boot after update 10.04 beta 2

---

### Post by skbhat03 on 2010-04-24
hi all, i did a successful upgrade to beta 1 from 9.10 some time back. But since few days, when i allow the regular updates (via update manager), ubuntu fails to boot ! i just get the initial screen with "ubuntu" logo and then it takes me to a black screen

i have also tried to do a clean install of beta 2, but after the update again same problem.

Now i tried with clean installation of RC1 and again same problem !.

First i though there is some problem with live CD. I checked it on another laptop and it worked fine. But not on mine :(


Best regards,
Subbu.

---

### Post by yakitori3 on 2010-04-24
tried rc1 hoping it would be the solution...had to go back to Karmic for now which is working fine

---

### Post by skbhat03 on 2010-04-24
RC1 same problem :(
Hope it will be fixed in RC2

---

### Post by yakitori3 on 2010-04-28
Just checking if there is more information....Need to go forward to 10.04

---

### Post by yakitori3 on 2010-04-29
Does anyone know if things have been fixed? I hate to try an update and have that problem come back.

---

### Post by yakitori3 on 2010-04-29
I have a Dell 700m  What other computers is this a problem for?

---

