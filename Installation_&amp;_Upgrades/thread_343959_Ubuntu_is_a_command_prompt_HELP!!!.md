---
title: "Ubuntu is a command prompt HELP!!!"
date: 2007-01-22
forum: Installation &amp; Upgrades
---

### Post by englandc299 on 2007-01-22
Help.  My laptop has a usb cd rom drive and i cannot boot off this unless there is a way i dont know?  I tried the network install method and it used my existing internet connection and router to connect to the internet and download what is required.  Ubuntu installed ok but when i eventally got onto ubuntu it was a command prompt.  I believe this may be a graphical issue.  Ubuntu worked ok last time i had it on my pc i dont know why i doesnt work now?

Thanks

---

### Post by renzokuken on 2007-01-22
have you tried typing 

```
startx
```

at the command prompt, may just be that because of the way you installed its not setup to automatically use X

---

### Post by JamieC on 2007-01-22
If that doesn't start the graphical X server, you'll need to install a desktop meta-package:
```

sudo aptitude install ubuntu-desktop

```

---

