---
title: "can't fix broken packages"
date: 2010-12-13
forum: Installation &amp; Upgrades
---

### Post by chkneater on 2010-12-13
I am trying run an update but I get an error "Fix broken package first".

I then went into synaptic and fixed the broken packages and tried to the update but I had the same problem still.  

Is there another way to fix packages with a terminal command?

---

### Post by Quackers on 2010-12-13
You could try
```
sudo dpkg --configure -a
```

---

### Post by Rubi1200 on 2010-12-13
Try running the following commands (post back if errors are reported; copy/paste from the terminal):

```
sudo apt-get install -f

sudo dpkg --configure -a
```

edit: oops beaten by Quackers...again :-)

---

### Post by Quackers on 2010-12-13
Lol, but I only had half of the options :-)

---

### Post by chkneater on 2010-12-13
I didn't get any errors and sudo apt-get install -f  came out with 0upgraded 0 newly installed, 0 to remove and 320 not upgraded.  Any thing else I can do?

---

### Post by matt_symes on 2010-12-13
Hi

Open a terminal and type

sudo apt-get update
sudo apt-get upgrade

Post back any errors.

Kind regards

---

### Post by chkneater on 2010-12-13
I ran the code and came out with no errors then went to try to update and I got the same error.  There was one more thing that said that no more updates will be made available.

---

### Post by Quackers on 2010-12-13
Which version of Ubuntu are you running?

---

### Post by chkneater on 2010-12-13
9.04

---

### Post by Quackers on 2010-12-13
Non LTS versions of Ubuntu are only supported for 18 months I believe.

---

### Post by chkneater on 2010-12-13
I figured that's what it was but thanks for varifying it for me.  I'll jus go and upgrade.

---

