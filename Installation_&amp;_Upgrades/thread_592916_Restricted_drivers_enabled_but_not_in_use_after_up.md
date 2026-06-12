---
title: "Restricted drivers enabled but not in use after upgrade to Gutsy"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by Ezabel on 2007-10-26
Hi, I've just updated to Gutsy, and everything seems to be working fine, except the restricted drivers (which affect both my wireless and desktop effects). Using the newest kernel, there are two drivers that are enabled, but it says 'not in use' after a big red dot. Would anyone happen to know how to make them in use? The restricted drivers that are not in use are the ATI accelerated graphics driver and some driver for a modem (which I don't really need). The wireless driver seems nowhere to be found at all... (my wireless card is an Intell PRO/Wireless 2200 BG)
Hope this all makes sense, any help is very much appreciated!!
:KS

---

### Post by chatterbox101 on 2007-10-28
Hi Ezabel,

I've just been through this, slightly differently as it was a manual install of the driver, but exactly the same symptoms with the enabled but not in use problem.

I typed this in a terminal:

```
sudo depmod -a
```

then restarted X (Ctrl-alt-backspace)

Seemed to do the trick...now enabled and in use :)

---

### Post by Ezabel on 2007-10-29
That worked beautifully, thanks for your help!! Now I can finally start enjoying the desktop effects :).

---

### Post by joelswanson on 2008-05-01
I have the same problem, but the above did not work for me.  Any other ideas?

---

