---
title: "Changes to installtion"
date: 2010-04-15
forum: Installation &amp; Upgrades
---

### Post by PaulClarke on 2010-04-15
Hello,

I have just taken over my wife's laptop and wish to change a couple of things.

1.  The computer auto boots to Julie's desktop without logging in.  How do I change that to the normal log in screen?

2.  I know I am fussy but the the computer is called Julie-laptop.  I have changed the samba file so the netbios is now Paullaptop but does this change the computer "name"

Thank you

Paul

---

### Post by deeminter on 2010-04-15
To change from automatic login to a login screen do the following: Under System, select Administration, then select Login Screen. Once The Login Screen Settings come up, unlock the settings using the Administrator password. Once the settings are unlocked, select Show the screen for choosing who will log in. Hope this helps.

deeminter

---

### Post by PaulClarke on 2010-04-16
deeminter

That worked a treat

Thank you

---

### Post by nothingspecial on 2010-04-16
Change the name in /etc/hosts and /etc/hostname

---

