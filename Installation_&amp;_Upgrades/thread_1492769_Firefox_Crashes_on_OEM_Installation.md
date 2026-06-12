---
title: "Firefox Crashes on OEM Installation"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by carlexpc on 2010-05-25
Hi Everyone!

I tried to install Lucid via OEM installation. I applied the updates and initially tested Firefox. I've noticed that the browser crashes (closes unexpectedly) if I try to click on a link on the default home directory ([http://start.ubuntu.com/10.04/Google/](http://start.ubuntu.com/10.04/Google/)). I also tried accessing other sites, they load successfully but crashes when I start to click on a link.

I checked the logs and there's no message that could possibly help me figure out the problem. I could not check for crash logs on Firefox via about:crashes because even executing about:crashes on the browser crashes the program. 

I even tried uninstalling Firefox and reinstalling it but the crashing still happens.  

Firefox version: 3.6.3


Any help you could extend is greatly appreciated.

---

### Post by cariboo on 2010-05-25
Try creating a new firefox profile to see if you run into the same problem.

```
firefox -Profilemanager
```

---

### Post by carlexpc on 2010-05-25
Thank you for your reply cariboo907.

I was able to solve my problem prior to reading your post. I removed Moonlight plugins and reset the default Firefox profile. 

The moonlight plugin was the culprit. I'm permanently removing it and it's no use for me anyway.

---

