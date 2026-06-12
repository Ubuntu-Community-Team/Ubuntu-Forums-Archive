---
title: "Avahi .local error notification"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by aamukahvi on 2009-03-29
How do I make this stop? I've tried searching for an answer.
> [2009-03-29T17:23:49-00:00, update-notifier ] Network service discovery disabled
Your current network has a .local domain, which is not recommended and incompatible with the Avahi network service discovery. The service has been disabled.
I get it on every login.

---

### Post by jruden on 2009-04-07
I get the same and I don't understand it either. Have you found any clues about this yet aamukahvi?

---

### Post by olskar on 2009-04-07
I used to get this back in Intrepid but only once after the first time connecting, now I get it every boot just like you. Annoying. 

Workaround that might work, haven't tried yet;

sudo rm /var/run/avahi-daemon/disabled-for-unicast-local

Also look at the bugreport and click "This bug doesn't affect me (change)", leave a comment if you like.

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362](https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/327362)

---

### Post by aamukahvi on 2009-04-07
Thanks, tried "host -t SOA local" and indeed Sonera DNS does have an entry for this...

---

