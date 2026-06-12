---
title: "[WORKAROUND] ibex+nomachine+bad keys sent"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tigerstripedcat on 2008-10-12
If someone knows the exact cause of this problem it would be nice to narrow down so I know who to submit the bug to

problem:
with a 8.10 client if you log into an 8.10 server with nomachine some keys are mapped incorrectly ( R_crtl is "~" and the arrow keys don't work.  If the client is 8.04 this problem does not occur, if you use nxclient for windows the problem does not occur.  If you do xmodmap -pke | grep 113 and the line is blank or wrong (it shoudl say "Left") then you have the problem.


I'm not quite sure of what causes this problem: nomachine or intrepid

workaround:
from the client run:
xmodmap -pke > xmodmaptemp
transfer xmodmaptemp to server
after logging in run xmodmap xmodmaptemp

this should reset your keys to the correct values.

---

### Post by forumache on 2008-10-13
tiger, you are great!
my work machine has a UK keyboard and the home machine has a US keyboard with Romanian layout. Of course I had problems ;)

Your solution works for me and I thank you.

---

### Post by pincushionman on 2008-10-28
Please report the bug to No Machine, I think the problem is with NX.  I can't find their bug tracker, but I know that they had this problem once in the past in the 2004 timeframe - numlock/arrow keys reversed. Interestingly, when no machine is active, and I have not done the xmodmap patch, NumLock has to be on before the arrow keys work on my dedicated number pad (this is a laptop, and using the keyboard number pad is painful).

I tested it by logging into a Red Hat Enterprise Linux 4.0 box (from Ubuntu's and from Vista's NX client) - same problem with keys that your xmodmap patch mostly fixes (you may have to modify some XF86modifier keys out if you have a laptop or multimedia keyboard).

Also logging into NX server 3.2 on OpenSuSe produced the same results.  I can't remember if NX  3.0 or 3.1 had this behavior (I don't think so...) So I'll have to keep the xmodmap on hand to get this fixed.

Thanks for the workaround!

---

### Post by rdoolen on 2008-10-29
Does this workaround effect the keyboard during other sessions, like from a Windows XP client or working at the server itself? Would I need to run the xmod command each time I login?

---

