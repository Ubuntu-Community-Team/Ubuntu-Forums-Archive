---
title: "Help needed installing GoogleEarthLinux.BIN"
date: 2007-10-09
forum: Installation &amp; Upgrades
---

### Post by ronfree on 2007-10-09
Newby needs help!  I just loaded KUBUNTU 7.04 and everything seems to run great.  I read the post on installing .BIN files, but still won't work for me.  Can't this be done in "Add / Remove New Programs" or "Adept"??  Any help on how to install GoogleEarthLinux.BIN will be appreciated.  Thanks! 
PS: KISS (Keep it simple (for) stupid)

---

### Post by Pumalite on 2007-10-09
Properties>Executable>Double click

---

### Post by fallingleaf on 2007-10-09
Add this line to /etc/apt/sources.list:
```

deb http://packages.medibuntu.org/ feisty free non-free

```

then

```

sudo aptitude update
sudo aptitude install googleearth

```

Or if you want you can use adept.  "Adept" menu->Manage Repositories.
Click on "Third Party Software", Add.

Paste in:
```

deb http://packages.medibuntu.org/ feisty free non-free

```

---

### Post by Pumalite on 2007-10-09
You can 'google' google earth for linux, download the file and do what I said in post # 2

---

### Post by ronfree on 2007-10-10
Thanks to all replies.  I used:  sh GoogleEarthLinux.bin in a terminal and it worked very well.  Only problem I have is that GoogleEarthLinux is sooooooooo slow.  Seems others have the same problem.  I can always (arrrgggghhh) resort to Windows.

---

### Post by jimrz on 2007-10-14
> **ronfree said:**
> Thanks to all replies.  I used:  sh GoogleEarthLinux.bin in a terminal and it worked very well.  Only problem I have is that GoogleEarthLinux is sooooooooo slow.  Seems others have the same problem.  I can always (arrrgggghhh) resort to Windows.

sounds like you have an ati card. my mobility 9600 has the same issue in feisty and have not yet installed gutsy (probably will next weekend, as gutsy on my desktop is great). have heard that the new ati drivers are somewhat better and that the next version (soon, I hope) will likely cure the issue <fingers-crossed>

---

### Post by fferreira on 2007-11-17
> **fallingleaf said:**
> Add this line to /etc/apt/sources.list:
```

deb http://packages.medibuntu.org/ feisty free non-free

```

then

```

sudo aptitude update
sudo aptitude install googleearth

```

Or if you want you can use adept.  "Adept" menu->Manage Repositories.
Click on "Third Party Software", Add.

Paste in:
```

deb http://packages.medibuntu.org/ feisty free non-free

```

I did exactly this, but I keeping receiving SF every time I try to execute Google earth on Gutsy....

Any Idea?

---

