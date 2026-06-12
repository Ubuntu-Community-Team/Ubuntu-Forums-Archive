---
title: "Very new to ubuntu 9.10"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by keema on 2010-02-28
Good Morning/Evening :p

Im a new member and new as well to ubuntu. I've installed the ubuntu 9.10 karmic koala in my laptop (fujitsu siemens amilo pro v3405). installation went well but it did not installed my wireless card, i think ;)

i checked my wireless card model and it is a intel pro/wireless 3945ABG. I have downloaded it and saved it in the downloads folder but i dont know how to install it? 

anyone here would help me how to install it?

thanks..:)

---

### Post by Toaster Box on 2010-02-28
i have the same problem with my laptop you.
to make your wireless function correctly you must connect to a wired internet cable and download the wireless drives in system>administration>hardware drives

---

### Post by mikewhatever on 2010-02-28
> **Toaster Box said:**
> i have the same problem with my laptop you.
to make your wireless function correctly you must connect to a wired internet cable and download the wireless drives in system>administration>hardware drives

No you don't, at least not _intel pro/wireless 3945ABG_. That card should work out of the box.

keema, check the wireless on/off switch first. If that's not the problem, please post the output of the following from Application->Accessories->Terminal:

sudo lshw -C network

---

