---
title: "Difference between Desktop and Server?"
date: 2007-02-15
forum: Installation &amp; Upgrades
---

### Post by Sicilianmandolin on 2007-02-15
I'm curious as to what the difference is between the Desktop and Server editions of Ubuntu. I'm considering downloading the Server edition because I want to gain experience with dealing with servers, but I don't want to have to sacrifice anything the Desktop edition might have that the Server doesn't. Is the Server edition pretty much just the Desktop edition with server capabilities?

Thanks!

---

### Post by Qrk on 2007-02-15
Nope, it lacks a desktop and other goodies. Its designed to be lightweight but not very user friendly. 

If you'd like a desktop system which you could then use as a server, I think your best bet would be just to download the desktop cd and install the server packages you want (apache, mysql, etc are all available in synaptic)

---

### Post by Kateikyoushi on 2007-02-15
No not at all the server is meant to be used on a server, uses the debian text based installer, it won't install graphical user interface either, so I would rather recommend go for the desktop and install the apps you want to be familiar with.

---

### Post by Sicilianmandolin on 2007-02-15
Ok, great advice. Thanks again.

---

### Post by JensenDied on 2007-02-15
I do this backwards, but then again im on a laptop with a nearly half dead battery (65% is now the max charge) but I install a command line system first, then install packages as needed **(not recommended for people who dont know their way around a prompt)**

---

### Post by GoingDown on 2007-02-15
All ubuntu software can be installed to server version as well, there is no real difference.

Only differences I have found:

* kernel version uses different kernel package which is just configured to be more suitable for servers (you can change to desktop kernel by apt-getting desktop kernel and then removing server one)
* kernel version doesn't install graphical interface by default. If you can handle command line, you can easily install base desktop by installing meta package ubuntu-desktop, which should take care of everything

Usually I like to install plain version first (=server), and then I just apt-get packages which I need.

---

### Post by Kateikyoushi on 2007-02-15
That's true guys and I would rather do that as well but if he has to ask probably he could not do it.

---

### Post by Sicilianmandolin on 2007-02-15
Yes, I'm an Ubuntu newbie. I haven't even installed the program yet. :???:

---

### Post by Kateikyoushi on 2007-02-15
That's why I recommended the other way around which is easier the difference isn't that big you can always trim down the unneeded installed softwares and learn something in the process.

---

