---
title: "How to connect EVDO to internet without wvdial in jaunty"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by sonu 1807 on 2009-03-28
I downloaded the beta release of jaunty and installed it on a separate partition. In intrepid I  connected to internet using wvdial and then installed kppp. But in jaunty wvdial is missing. My wired connection has not been working and without loading hardware driver I can not connect to internet using wireless. I tried pppconf but can't get it to work. The "plog" command shows some error. Now I have two questions
 
1. Is their any workaround to install wvdial in jaunty ? Simply downloading wvdial package failed as it shows dependency error

2. I hope they are not going to drop wvdial altogether in jaunty final release. Are they ?

---

### Post by sonu 1807 on 2009-03-28
No replies ? :(

---

### Post by sonu 1807 on 2009-03-28
Should I have given " I am leaving Ubuntu" or "Ubuntu sucks" as the title of this thread to get replies?

---

### Post by digitalmonk on 2009-03-28
thank God,on second thoughts I opted not to migrate to jaunty beta, i too use bsnl's usb internet.will upgrade to the karmic koala in 9.10

---

### Post by sonu 1807 on 2009-03-28
I installed it on a separate partition. I am typing this from intrepid

---

### Post by sonu 1807 on 2009-03-28
Got it working

1.sudo pppconfig
2.gave the connection name as ZTE
3.entered username and password
4.specified modem as /dev/ttyUSB0 (earlier I was giving ttyS0)
5.Saved and then  quit
6.Became root and then connected using pon ZTE
6.Then installed Gnome PPP

Jaunty looks impressive. Obviously there is an improvement in the boot time

---

### Post by mingtien on 2009-04-21
So does this mean that in the version of Network Manager that comes with Jaunty, EVDO/CDMA is still not fixed?

---

### Post by electricroo on 2009-04-21
Network manager EVDO did not work with the alpha and beta builds with my netbook. I waited a week and went back to the daily build and it has been working properly ever since. I have not upgraded my desktop yet but I'm about to.

---

### Post by jheaton5 on 2009-04-22
Network Manager (7.0) since Intrepid and now in Jaunty simply recognizes my EVDO and connects.  No configuration of wvdial.conf was nessary.

---

