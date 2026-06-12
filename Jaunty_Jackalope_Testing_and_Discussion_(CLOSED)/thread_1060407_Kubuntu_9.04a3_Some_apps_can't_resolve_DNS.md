---
title: "Kubuntu 9.04a3: Some apps can't resolve DNS"
date: 2009-02-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by David Gerard on 2009-02-04
My Linux partition is now Kubuntu 9.04 alpha 3. It hasn't gotten past that because it refuses to resolve DNS in apt - can't find security.ubuntu.com or gb.archive.ubuntu.com. Or in Firefox - I'm writing this from Konqueror.

ping and nslookup resolve names fine. Pinging the name before apt-get didn't work. Reboot and using Ethernet instead of wifi didn't work. Any ideas what's going on here?

---

### Post by agim on 2009-02-04
Sorry, I can't help. Other than that obvious issue, how is the alpha working out for you?

---

### Post by David Gerard on 2009-02-04
Well, so far KDE 4.2 is very pretty. I'd love to be able to say more about it, but that would require it to be working ;-p

---

### Post by David Gerard on 2009-02-06
Now on alpha 4, still doing the same broken stuff. What on earth?

---

### Post by cl333r on 2009-02-06
Firefox failed to find some hosts, after I went to about:config and disabled the "ipv6" property, it started working fine. I suppose same issue could be having Jaunty, cause I also experienced this issue until I changed the "software sources" to point to another country which's server Jaunty could find.

Jaunty alpha 4 is the first Ubuntu distro (using Linux since Feisty) where my HP 1020 printer works out of the box.
Some apps like vlc had bad dependencies so I was stuck with totem.

The audio is glitchy (very glitchy for the first time) but I'm sure the developers know about it (never happened in before, so must be a temporary mistake).

---

### Post by David Gerard on 2009-02-06
> **cl333r said:**
> Firefox failed to find some hosts, after I went to about:config and disabled the "ipv6" property, it started working fine. I suppose same issue could be having Jaunty, cause I also experienced this issue until I changed the "software sources" to point to another country which's server Jaunty could find.

That sounds promising. Did you get apt-get to work? I tried dropping the ipv6 address in ifconfig, but that didn't help.

---

### Post by cl333r on 2009-02-06
My workaround was (as I said) - I went to System->Administration->Software sources and have chosen another server. Fortunately Jaunty didn't have problems resolving the DNS of that server, and yes, apt-get started working.

---

