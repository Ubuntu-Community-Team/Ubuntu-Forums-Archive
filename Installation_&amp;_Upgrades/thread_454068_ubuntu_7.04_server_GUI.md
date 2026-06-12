---
title: "ubuntu 7.04 server GUI?"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by JackScript on 2007-05-25
Hello

I recently installed a server 7.04 and I was wondering how can I get it to run with a GUI environment. 
If it is possible, can I know what should I do.

thanks.

---

### Post by stefaan.dutry on 2007-05-25
For as far as i know:  server editions don't have a GUI.

---

### Post by ikonia on 2007-05-25
the server build does not ship with X windows installed

if you require one ask your self if you should be running a server.

if you really need one

```

sudo apt-get install gnome-desktop

```

will install one for you.

---

### Post by StanleyPoh on 2007-05-25
Well WHY NOT?

A small based-GUI just for the purpose of routine setting and administrating work is nice to have.

But do try WEBMIN first.

---

### Post by danboland on 2007-05-28
> **StanleyPoh said:**
> Well WHY NOT?

If your just fulling around with a server; i.e. testing stuff out, then no; it doesn't matter.  if your building a server for any type of production use: it very unwise.

X adds a lot of great features, but even more security holes and system resource usage.  This is one of the reason why the next version of Windows Server won't have to have a GUI installed.

if you have to install Webmin, swat... 
but you can do a lot more with the command line.

---

