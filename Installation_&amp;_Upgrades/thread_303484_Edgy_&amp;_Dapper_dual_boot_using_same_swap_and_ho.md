---
title: "Edgy &amp; Dapper dual boot using same /swap and /home ?"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by roots on 2006-11-20
hi everybody,

i'm on the drake since it first spread its wings and i just got curious about adding some eft to my life. so the question is whether it's possible to have BOTH as dual boot using the SAME /swap and /home ?!

anyone?

cheers,
roots.

---

### Post by BLTicklemonster on 2006-11-20
Good question...

---

### Post by roots on 2006-11-20
if i didn't need the machine for work very badly atm i'd give it a try right now...

---

### Post by ReaderRat on 2006-11-20
Yes, you can use the same /swap.....don't know about /home.

---

### Post by ajgreeny on 2006-11-20
Same swap, no problem;  same /home could give some difficulties as a result of different versions of software packages.

---

### Post by roots on 2006-11-20
hmmm actually my concerns were rather towards sharing /home as there will be different versions of applications accessing it, eg. evolution etc. so i don't know if that will end up in a terribly mixed mess...

---

### Post by melancholeric on 2006-11-20
It is possible to share /home if it's on a separate partition. No idea about /swap though.

edit: [http://linux.oneandoneis2.org/starting.htm](http://linux.oneandoneis2.org/starting.htm)

---

### Post by roots on 2006-11-20
hehe...ajgreeny was a bit quicker with that...

anyway, melancholeric - did you try? did you mean it'll work if /home is on a different partition than / is?

---

### Post by roots on 2006-11-20
> **melancholeric said:**
> It is possible to share /home if it's on a separate partition. No idea about /swap though.

edit: [http://linux.oneandoneis2.org/starting.htm](http://linux.oneandoneis2.org/starting.htm)

ok, thanks a lot for that link! i think i'm gonna give it a try when i get the time and let you know if it worked out...

thanks a lot!
cheers,

roots.

---

### Post by shane2peru on 2006-11-28
How did it work out?  I was thinking of the same thing, however I was thinking of having a separate user for each distro.  This would really keep them separate, wouldn't it???

Shane

---

### Post by timcredible on 2006-11-28
i have ubuntu and pclos on the same PC, they share swap and /home.  you have to have a separate partition for /home to do this.  install one distro, then the other.  the only tricky part was getting lilo or grub to work, because you have to manually edit it and have the linux kernel from the distro you loaded first from a mounted partition other than / (because you can only mount one of the distros root partitions at /, but it re-mounts properly after the kernel loads).  if i remember, i'll post my lilo.conf file when i get to that machine tonight.

---

### Post by shane2peru on 2006-11-28
Yeah, I'm currently triple booting.  I was more curious about the home situation.  Do you have 2 different users?  or do you use the same for both distros?  Does it create problems with your desktop settings?  Thanks!  - I really think I'm going to go with two separate user names.

Shane


PS, my /home is a separate partition for my main distro.  I have the other one separate.

---

### Post by shane2peru on 2006-11-28
Don't do what I did.  When I boot into Dapper now, it will not let me access my other user.  The boot screen doesn't look the same either.  The nice thing is now I'm using Edgy, and going to port all my stuff over from other /home/user.  I hope Edgy works nicely with my system.  - I will be re-installing all my programs again. 

Shane

---

