---
title: "Weird error trying to boot 7.4 live disk, Please help"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by xzyle on 2007-10-04
I am trying to install ubuntu 7.4 on a brand new laptop. I keep getting a weird error when trying to start up the live disk. I can get to the selection menu, but not much farther then that. After selecting Load or Install, I get the loading screen and then it stops and I get this message on the screen.

Busybox v1.1.3 (Debian 1:1.3-3Ubuntu3) Built-in shell (ash)

/bin/sh: can't access tty; job control turned off


 I have tried a couple different thing and still haven't gotten anywhere. I'm still fairly new to Linux so any help would be great.

 This laptop is an ESC with an Intel  Core2 Duo, 2Gigs of Ramm, and a 60Gig Sata HDd. i don't know if this will help.

 Thanks.

---

### Post by Pumalite on 2007-10-04
Try:

At the LiveCD initial boot screen:
Select F6 for more options
Add the following option to the beginning of the options list:
break=top
Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

If not, then try Alternate CD.

---

### Post by xzyle on 2007-10-05
Tried that. I get further along until the X dies. it tells me that there wasn't a screen found. Which is really weird. I'm downloading the alternate cd and the new 7.10 and see if one of those work.


Thanks

---

### Post by Pumalite on 2007-10-05
Ok.

---

