---
title: "Flash Player Plugin on Linux 11.2.202.424"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by TI9 on 2014-12-14
Hello, need help, I'm new. 

Adobe flash player plugin needs to be updated, security issues. I've downloaded from ([https://get.adobe.com/flashplayer/](https://get.adobe.com/flashplayer/)), into my downloads. It's in (tar.gz), I'm not sure what to do next. I'm not sure how to update the plugin, for firefox. Archive manager, just came up, see attachment below.

I am not sure how to use (file roller or archive manager), looked over the help, not much there, what do I do?

Not sure if I should (open new), (add files) (extract). Is there an order to this? Where, do the added or extracted files go?

I really need help.

Thanks

---

### Post by QIII on 2014-12-14
You may potentially cause issues with your package manager if you do that.  Best to use what is in the repository.

What release of Ubuntu are you using?

Just by way of explanation:  Some websites are going to complain about your version of Flash no matter what you do.  Adobe stopped development of the Flash Player for Linux a couple of years ago and now all we get is security updates for 11.2.  If a website expects a later version, it will continue to report that you need to update Flash even if you have the latest Linux security updates.

Are you getting the message on specific sites or everywhere?

---

### Post by deadflowr on 2014-12-14
How'd you install it in the first place?
From Adobe or did you install it using any number of methods from the Ubuntu software installers( the software center, synaptic, a command line, etc)

If you install flash through the Ubuntu way, then simply update your system.
It'll update the plugin for you.

---

### Post by TI9 on 2014-12-14
I'm using 14.04 Xubuntu. I am getting that message on firefox, Even when I tried to upload the photo.

---

### Post by QIII on 2014-12-14
deadflowr asked a pretty good question:  How did you install Flash to begin with?

---

### Post by TI9 on 2014-12-14
From the Ubuntu software center. There is a new security update.

[https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796](https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796)

---

### Post by QIII on 2014-12-15
Have you done updates lately?  That should have been updated.  I have 11.2.202.425

---

### Post by deadflowr on 2014-12-15
> **TI9 said:**
> From the Ubuntu software center. There is a new security update.

[https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796](https://blocklist.addons.mozilla.org/en-US/firefox/blocked/p796)


Which has a new security update, Ubuntu or Firefox?
If Ubuntu what is it?

---

### Post by TI9 on 2014-12-15
Yes, today, no new updates avaliable. I was hoping it would update to 11.2.202.425, so I don't have to use that (tar.gz)

---

### Post by TI9 on 2014-12-15
It is with Firefox, it's a ( shockwave flash 11.2.202.400 ) plugin update. see attachment

---

### Post by deadflowr on 2014-12-15
Try a quick terminal update method
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by TI9 on 2014-12-15
Thanks, deadflowr and QIII for your help. Still not sure what to do.

---

### Post by TI9 on 2014-12-15
Thanks, deadflowr, just saw the update. Tks for the code, I'll try it.

---

