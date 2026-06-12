---
title: "firefox offline issue"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by unix1adm on 2010-05-10
After my upgrade from 9 to 10 firefox keep coming up set to work offline. 

Why??? 
I have a valid network connection and i turn off work offline option and it connects fine. 

Why is is launching as workoffline???

---

### Post by unix1adm on 2010-05-11
no one has seen this issue before?

I have checked all over for the setting. If I look under the File menu it shows a check next to work offline as stated above but I uncheck it and it comes back. I killed the process from a PS command and it still comes back. tried a close from the file menu and it still comes back. May be something got munged in a cfg file on the laptop???

---

### Post by unix1adm on 2010-05-11
I found this but its and older version of FF. 
[http://blog-on-linux.blogspot.com/2009/02/firefox-starts-in-offline-mode.html](http://blog-on-linux.blogspot.com/2009/02/firefox-starts-in-offline-mode.html)

Did not seem to help

I did try this. But have not rebooted yet to confirm it works. Will report back later. 

"I had the same issue and after googling it, I found you can fix this by setting "toolkit.networkmanager.disable" property of Firefox to "true". Type about:config in the address bar and copy and paste toolkit.networkmanager.disable there and set its value to true by double clicking on it. I even blogged it. Hope this will help you :) "

---

### Post by unix1adm on 2010-05-13
the above seemd to work for this issue

---

