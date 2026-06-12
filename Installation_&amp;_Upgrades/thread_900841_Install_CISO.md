---
title: "Install CISO?"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by Mecharuva on 2008-08-25
[http://linux.softpedia.com/get/Utilities/Ciso-32141.shtml](http://linux.softpedia.com/get/Utilities/Ciso-32141.shtml)
^Link to download
So I download this to /home/mecharuva/Downloads,
Open Terminal,
CD there,
"tar -xvzf '*cisofilehere*'"
All goes well.
'Cept now I try "./configure" and it says "No such file or directory."
:(
I'm on the latest Ubuntu, KDE - if it matters.
I have XFCE and Gnome too.

---

### Post by sisco311 on 2008-08-25
ciso is in the repositories.
You can install it from Synaptic Package Manager, Add/Remove... or 
from the terminal:
```
sudo aptitude install ciso
```

---

### Post by Mecharuva on 2008-08-25
Blagh I tried Add/Remove earlier and it couldn't find CISO.
Shoulda tried the aptitude command then, my bad.
Thanks.

---

### Post by sisco311 on 2008-08-25
Enable the *universe *repos, then try again.
[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

---

### Post by Mecharuva on 2008-08-25
They're already enabled.

---

