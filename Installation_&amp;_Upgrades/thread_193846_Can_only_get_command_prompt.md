---
title: "Can only get command prompt"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by thelarster on 2006-06-10
I'm a newbie so take 'er easy on me. My first install went good for Ubuntu 6.06 w/ no errors. But after rebooting it goes straight to the command prompt and I can't get to the GUI.

Any ideas why or how to get it started? I've tried startx and a few others.

---

### Post by FizDev on 2006-06-10
Did you do a standard or a server install?
If startx doesn't do anything. You might have to install it doing this :
```
sudo apt-get install ubuntu-desktop
```

---

### Post by thelarster on 2006-06-10
I did the standard install... I tried that and gives an error. Not home right now but I'll post the error later.

---

### Post by thelarster on 2006-06-12
I was wrong, I did do the server install. After downloading and doing desktop everything works fine. 

So you can't have a GUI interface w/ the server install? I was going to try Apache, PHP, etc. so I think that's why I picked that one.

---

### Post by taurus on 2006-06-12
Yes, you can still have window manager if you install the server version.  You just have to install it as
```

sudo apt-get install ubuntu-desktop

```

---

