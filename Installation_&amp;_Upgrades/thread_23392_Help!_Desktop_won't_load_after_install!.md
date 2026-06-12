---
title: "Help! Desktop won't load after install!"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by vioflex on 2005-04-01
Hi, i'm new here* and* with linux.
I've just installed Ubuntu in an old Pentium MMX 233 PC.
The problem is, after i'm asked the login and password, gnome doesn't load, only the same black screen as before with a message like this:

> 
Ubuntu comes with absolutely no warranty (...)
You have mail
nameofthepc: ~ $

What happened? Did I do something wrong?

---

### Post by fdoving on 2005-04-01
try to run this command:
```

sudo invoke-rc.d gdm start

```

If that doesn't do it, you'll have to make sure ubuntu-desktop is installed:
```

sudo apt-get install ubuntu-desktop

```

and make sure everything is configured, and reconfigure the xserver, just in case:
```

sudo dpkg --configure -a
sudo dpkg-reconfigure xserver-xorg

```

Then try to run gdm again:

```

sudo invoke-rc.d gdm restart

```

Good luck.. just my $1..

---

### Post by feneks on 2005-04-02
[QUOTE=vioflex]Hi, i'm new here* and* with linux.
I've just installed Ubuntu in an old Pentium MMX 233 PC.[/QUOTE]

:shock: P MMX 233 :shock:

How much RAM do you have. (Out of topic: god old edoRAM I suppose.)

I have an old PII Notebook using minimalistic Debian sarge with Winowmaker (instead of GNOME). This is with fast reactions but I cant imagine to use GNOME. Perhaps I should give it a try?  :-k

---

