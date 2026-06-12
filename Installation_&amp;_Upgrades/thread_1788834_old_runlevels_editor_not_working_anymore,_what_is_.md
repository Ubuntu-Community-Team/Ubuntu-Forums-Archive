---
title: "old runlevels editor not working anymore, what is the name of the new one ?"
date: 2011-06-23
forum: Installation &amp; Upgrades
---

### Post by Sorcerer25 on 2011-06-23
what is the name of the new startup/boot manager ?

i installed ubuntu server latest version
now services can be administrated via "service" command (no need any more to call /etc/init.d/servicename) ... all well and good ... but

how can i manage what service start when computer start ?
until now i was using sysv-rc-conf but now i see that what this boot manager does is ignored

for example: i installed samba, now there are 2 new services called nmbd and smbd, in sysv-rc-conf both are marked not to start (no "X" on any runlevel) but at reboot they are starting

and it can still be installed (sysv-rc-conf package), even if, from what i see, it does nothing any more


**[SIZE=2]so, how can i manage this ?[/SIZE]** and i'm first interested in command line/console solution

---

### Post by zvacet on 2011-06-23
See if [this]("https://help.ubuntu.com/community/UpstartHowto") can help you.

---

### Post by Sorcerer25 on 2011-06-23
right now i'm pissed off ! ... i just installed bum, ALSO NOW WORKING !

so, i just want a GOOOOOOOD and **WORKING** runlevel editor !
... maybe i ask too much !

also, sending one to manually removing links in /etc/rc*/ is not only **really lame**, is also **DANGEROUS !**
from oficial documentation
> 
rm /etc/rc*/*myscript
o yeah, like i'm gonna use that ... EVER ... one small mistake and all my etc is gone with all that "*" characters in it

now, what i see is just another "help me" with the answer "we can't be cause we changed things and DON'T CARE ABOUT DOING THE JOB RIGHT ... AND ALL THE WAY"
i guess i should be "really thankful" for things like service and update-rc.d are out there and working, not matter how little they do

at this point there is no doubt in my mind that you are doing this in purpose so people will see EXACTLY WHAT OPEN SOURCE IS and move to commercial 

SO ... "**WELCOME TO UBUNTU !"**

---

