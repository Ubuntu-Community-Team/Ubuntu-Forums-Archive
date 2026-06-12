---
title: "Edgy: cannot update due to network ..."
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by hdunnigan on 2008-08-17
...but I HAVE Internet: confused. I don't have the option appearing to update on my recent installation of Edgy Edge (the only CD I have) nor can I do any Add/Remove apps because of an unknown "network error." However, I am able to access the Internet just fine. I am at home with a direct connection to the cable modem, no router. I am posting this message from the Ubuntu machine, so it has Internet, but apparently some other network problem. What do I look for?

---

### Post by Mister.Vash on 2008-08-17
Can you post the exact error message?

Also, can you post the contents of your /etc/apt/sources.list file?

---

### Post by kostkon on 2008-08-17
Sorry, but Edgy is not supported anymore, and the repositories went down, that's why you get network errors.

But you can still use them, if you change your *sources.list* file to be like this
```
deb http://old-releases.ubuntu.com/ubuntu/ edgy main restricted

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy main restricted

deb http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy-updates main restricted

deb http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse

deb-src http://old-releases.ubuntu.com/ubuntu/ edgy universe multiverse

deb http://old-releases.ubuntu.com/ubuntu edgy-security main restricted

deb-src http://old-releases.ubuntu.com/ubuntu edgy-security main restricted
```

You'll have to open a terminal, give
```
gksudo gedit /etc/apt/sources.list
```
then comment all the existing lines (by putting a # at the start of each line) and then paste the lines above. Save the file and then do a
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by hdunnigan on 2008-08-17
Thanks for the replies, I will first try to get a  more recent ISO CD (should have done that first I suspect) and will keep the other ideas in mind. Appreciate the answers!

---

