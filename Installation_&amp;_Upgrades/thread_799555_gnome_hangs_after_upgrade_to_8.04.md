---
title: "gnome hangs after upgrade to 8.04"
date: 2008-05-19
forum: Installation &amp; Upgrades
---

### Post by jimrothstein on 2008-05-19
I seem to have messed up Ubuntu upgrade.

I can boot, get the Ubuntu splash screen, login (hear the music) and then system hangs.  Can't see the desktop.

-Had 7.04, upgraded to 7.10 and then Hardy
-upgraded from internet (not CD)
-only thing that works now is selecting Session - Failsafe terminal, i.e command line
-have tried to reinstall gnome (apt-get install gnome, etc.)
-have tried to recovery mode (repair) but nothing works
-made Live CD with .iso, but it won't boot
-fear I'm just making things worse

Appreciate any thoughts.

Thanks.

jim

---

### Post by hermes0710 on 2008-05-19
Try adding a new user and login. Does this still happen? If no then there are some settings kept back in your home folder from gutsy that messes up hardy.

---

### Post by jimrothstein on 2008-05-19
Thx for quick reply.

A new user does seem to work! (Gnome does not hang.)  But I must also use an older linux kernel still in GRUB.

Not sure what to do now.

jim

---

### Post by hermes0710 on 2008-05-19
> But I must also use an older linux kernel still in GRUB

What do you mean?

---

### Post by jimrothstein on 2008-05-19
In GRUB, I have a few Ubuntu kernels.

With the newest one (2.6.24-16-generic), the new user can login, hear the music and the gnome desktop appears - BUT it is frozen, nothing will work.  (Must use Cntl-Alt F2 to shut it down).

With older kernel (2.6.20-16-generic) in GRUB, the new user IS able to use the gnome desktop and it all seems to work.

---

### Post by hermes0710 on 2008-05-19
Had you manually installed any drivers for your box when on gutsy (=older kernel)?

---

### Post by jimrothstein on 2008-05-19
New drivers?  No, I don't think so.

---

### Post by Keith Klos on 2008-05-30
> **jimrothstein said:**
> I seem to have messed up Ubuntu upgrade.

I can boot, get the Ubuntu splash screen, login (hear the music) and then system hangs.  Can't see the desktop.

-Had 7.04, upgraded to 7.10 and then Hardy
-upgraded from internet (not CD)
-only thing that works now is selecting Session - Failsafe terminal, i.e command line
-have tried to reinstall gnome (apt-get install gnome, etc.)
-have tried to recovery mode (repair) but nothing works
-made Live CD with .iso, but it won't boot
-fear I'm just making things worse

Appreciate any thoughts.

Thanks.

jim

I am new to Ubunto having just installed 8.04 on a new harddrive on a Dell Dimension l500r.  Installation was just fine but on reboot have the same problem as above execpt I can get it to boot in Gnome Failsafe. It hangs after I put in the user name and passord.  I hear the music and then the screen gets garbled with faint multiple Hardy Herons and then it hangs.  I am totally new to Ubuntu and have been searching the forums and tried per below to add a new user but same result.  When I DO boot in GNOME failsafe mode everything seems to work OK (although I am still trying to understand the system so everything may not work).  Any thoughts?  Thanks Keith

---

