---
title: ".run install file just won't work for me"
date: 2005-09-14
forum: Installation &amp; Upgrades
---

### Post by SevenForever on 2005-09-14
Hey,
I downloaded PlaneShift today, I only found it in a .run format. I first tried simply executing it, but it opens with the default text editor and does nothing. I fooled around in the consol, but nothing works to get that thing installed.

Anyone know what I'm doing wrong?

Thanks.

---

### Post by mlomker on 2005-09-14
It probably isn't set as executable.

Try 

```

sudo chmod 755 whateverfile.run
sudo ./whateverfile.run

```

---

### Post by SevenForever on 2005-09-15
Thanks! That worked!

---

