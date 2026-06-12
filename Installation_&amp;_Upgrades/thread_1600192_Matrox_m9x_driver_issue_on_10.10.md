---
title: "Matrox m9x driver issue on 10.10"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by STOIE on 2010-10-18
Hi there,

I recently upgraded to 10.10 from 10.04 on my x86_64 system.
The upgrade went fine except it cannot load the driver for my Matrox M9148. ("m9x")

I simply get a "Cannot load driver" error. (there is more to it, will paste when I finish work)
Basically the driver is there and in place, it loads it but cannot use it.

When I go to reinstall the driver again manually, it dies with an error only supports Xorg up to 7.5
So, now I see this is an Xorg and driver compat issue.

I have reported it to Matrox and am awaiting a reply.

In the mean time though, since I need my machine working, is there anyway around the issue, or could I even roll back xorg to whatever it was in 10.04 to get the drivers working again?

Your prompt help would be vastly appreciated.

Thanks,
Aaron.

---

### Post by barlowrm on 2011-02-11
Hi there,

I am heving exactly the same problem as you. The m9x binary driver installer dies complaining that it cannot find an appropriate Xorg version.

Did you managed to solve this? Would you mind sharing your solution?

Thanks for your help,

Andrea.

---

### Post by STOIE on 2011-03-15
No solution.

This is killing me, I cannot update at all.
It's a 6 month old card that hasn't worked for 5 months.

Not like it was cheap either @ $700!

Pisses me off that Matrox, pretty much refuses to fix the issue.
Honestly, with the troubles I have been having, I don't think I would ever buy a matrox card again.

Can anyone just make this work please!

---

### Post by barlowrm on 2011-03-15
Hi,

I decided to downgrade to 10.04, and of course now it works. Looks to me like Matrox lagging behind. Probably not Ubuntu's fault, but still a pain for users...

Cheers,

Andrea.

---

### Post by fyerly on 2011-03-20
Hi,

I face to the same problem with a matrox M9120, the matrox script complains that Xorg version is not between 7.1 and 7.5. I tried to look in the script where this control is made, but it seems that the control is done on a binary part (only the first part is a real shell...). 

Did somebody get an answer from Matrox?

Best regards
Fabrice

---

