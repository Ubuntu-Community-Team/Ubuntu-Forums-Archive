---
title: "How do install Limewire"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by Cbotron on 2006-11-13
How I install Limewire?

---

### Post by taurus on 2006-11-13
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

And if you search here, you will find there are a few threads regarding installing and running limewire!

---

### Post by Cbotron on 2006-11-13
I can't install a rpm package with it. :(

---

### Post by taurus on 2006-11-13
With .rpm, you first need to convert it to .deb with alien and install it...

```
sudo aptitude update
sudo aptitude install alien
alien <filename>.rpm
sudo dpkg -u <filename>.deb
```

p.s.  Section 3 from the link above!!!

---

### Post by Cbotron on 2006-11-13
So I can't install then with Synaptic Package Manager?

---

### Post by taurus on 2006-11-13
Nope.  Has to be from a terminal, Applications -> Accessories -> Terminal...

---

### Post by Cbotron on 2006-11-13
I give up....](*,) 
I tried the command of what you told me and i'm lost now.

---

### Post by kdawg on 2006-11-13
Well you could always try frostwire.... its installable through the synaptic package manager, or you can download the ubuntu deb file from frostwire.com

---

### Post by taurus on 2006-11-13
> **Cbotron said:**
> I give up....](*,) 
I tried the command of what you told me and i'm lost now.
Okay, maybe I need to explain it again.  When you download things, it will usually save to your ~/Desktop unless you told it to save somewhere else.  Therefore, you need to change to that directory, ~/Desktop, first before you can run or install it.  So, open a terminal, Applications -> Accessories -> Terminal, again and do

```

cd ~/Desktop
ls -la  <--  you should see your limewire on that list!!!
sudo aptitude update
sudo aptitude install alien
alien <filename>.rpm  <--  you need to replace the exact name from the output of "ls -la" above for <filename>!!!
sudo dpkg -i <filename>.deb

```

---

### Post by Cbotron on 2006-11-13
I think i'm gonna go with frostwire.I'll try installing limewire when i'm more used to the linux enviromment.I am now finally free from Microsoft world of chaos.

Thnaks guys for the help.Really appreciate it.;)

---

