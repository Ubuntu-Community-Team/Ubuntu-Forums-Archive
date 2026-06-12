---
title: "personalization with kickstart ou debconf"
date: 2015-04-13
forum: Installation &amp; Upgrades
---

### Post by Minus63 on 2015-04-13
Good morning

i hope thah someone can help me for installing ubuntu-desktop 14.04 LTS with kickstart ou debconf. 

I have downloaded ubuntu-14.04.2LTS-desktop-amd64.iso.

i have a kickstart and debconf file for made my own config ubuntu install.

On the script i write the initial user name and is encrypted password

The problem is that even the encrypt password is on the kickstart or debconf config file, the interface of ubuntu-desktop always ask me inital use name and his password, and i don't want that the install prog do this.

If i use the same config file but using ubuntu-14.04.2LTS-server-amd64.iso, everything in the install is ok even the initial user name and password.

How can i do this install with ubuntu desktop?

Many thanks

Best regard

---

### Post by dino99 on 2015-04-13
the desktop installer will not let doing it; so the solution is to use the 'server' iso but without installing the apps met on server only. the mini iso is userfriendly

---

### Post by Minus63 on 2015-04-14
Thank you for your answer

It is a real pity that it is not possible with the desktop version
I  have ubuntu to deploy with a personalization and that would have been better by using directly the desktop version without passing by the server or mini version.

---

### Post by dino99 on 2015-04-14
you also can make a custom installation, then clone it

[http://superuser.com/questions/709176/how-to-best-clone-a-running-system-to-a-new-harddisk-using-rsync](http://superuser.com/questions/709176/how-to-best-clone-a-running-system-to-a-new-harddisk-using-rsync)

---

### Post by Minus63 on 2015-04-14
yes i can do it, but in my case i have differents PC configurations and differents hostname.

In my opinion, cloning a configuration is only useful for saving a server.

---

