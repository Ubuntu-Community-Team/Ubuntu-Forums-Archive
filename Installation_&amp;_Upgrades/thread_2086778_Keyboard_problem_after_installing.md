---
title: "Keyboard problem after installing"
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by Nocta2 on 2012-11-21
Hi guys,

I installed Ubuntu 12.10 using WUBI (alongside Windows XP). After the installation, the keyboard layout was set to arabic so I can't log in (I set a password when I executed WUBI).
I guess the problem is because I'm from Argentina, so the keyboard is set to AR.

I can only log in as guest but that's all I can do but I can change the keyboard layout from that account.

I'll appreciate your input.

Thanks!.

---

### Post by bcbc on 2012-11-22
What happens if you drop to a terminal (Ctrl+Alt+F1)? Is it still arabic? If not, try:
```
sudo dpkg-reconfigure keyboard-configuration
```

---

### Post by Nocta2 on 2012-11-22
Sorry, I forgot to say it.

Yes, I tried that and it's in arabic too :/ It's a real pitty.

---

### Post by bcbc on 2012-11-22
Try reinstalling by running on the command line:
```
wubi.exe --language=en
```

Reference: [askubuntu.com/questions/193449/how-can-i-run-the-wubi-installer-in-a-different-language]("http://askubuntu.com/q/193449/14916")

PS don't forget to file a bug: bugs.launchpad.net/wubi/+filebug

---

### Post by Nocta2 on 2012-11-22
Alright. I'll try it and come back with the results.

I'm about to submit the bug.

Thanks!

---

### Post by Nocta2 on 2012-11-26
I installed it with "--language=en" but the keyboard layout was in arabic again.
The difference now is that I could change the arabic keyboard on-screen to english, so I logged in and changed the default layout.

Thanks.

---

