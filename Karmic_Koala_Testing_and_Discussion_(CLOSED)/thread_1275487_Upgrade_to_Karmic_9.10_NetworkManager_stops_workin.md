---
title: "Upgrade to Karmic 9.10 NetworkManager stops working"
date: 2009-09-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Enigmatist on 2009-09-25
Hi Everyone,
 
I was a Jaunty user since its initial release and enjoyed Ubuntu very much. Yesterday I decided to upgrade to Karmic 9.10 Alpha for a test run. However the following problem resulted:
 
I cannot connect to internet through ethernet OR wireless. The NetworkManager disappeared from the notification area. It complained about a "libnm-glib-vpn.so.1" missing so I followed a post about using the command: [ ln -s /usr/lib/libnm-glib-vpn.so.1 /usr/lib/libnm-glib-vpn.so.0]. Now the nm-applet shows up in the notification area with the text: "NetworkManager is not running..."
 
When I try to start NetworkManager there are no complaints, just nothing changes and I'm still unable to get wireless working. (However, I can access the network settings)
 
Has anyone experienced a similar condition or can shed any light on the situation.
 
On the other hand, I've been looking for a way to connect to wireless networks or ethernet lines through command line only (terminal) which may perhaps allow me to update and fix the problem.
 
Thanks all.

---

### Post by Enigmatist on 2009-09-28
anyone? please help?

---

### Post by !nkubus on 2009-09-28
Same here, it connects , but no icons on the systray.,

---

### Post by zika on 2009-09-28
Yo might want to look at a thread that was about that problem, with solution.
[http://ubuntuforums.org/showthread.php?t=1274185](http://ubuntuforums.org/showthread.php?t=1274185)

---

### Post by dentaku65 on 2009-09-28
What happens if type in a terminal:
```
nm-applet
```
?

---

