---
title: "automatic start up init.d"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by brigux on 2007-05-30
Hello!

I recently installed fail2ban manually (0.8.0). Unfortunately 0.8.0 does not install automatic startup script.
I therefore created a link to /usr/bin/fail2ban-client in init.d
as in:

ln /usr/bin/fail2ban-client fail2band 

I thought that would be enough to run 
fail2band start 
at boot but apparently it's not (running "$sudo fail2band start" does work tho)

What else do I need to do in order to have a script starting automatically at boot on feisty?

Thanks in advance.

brigux

---

### Post by brigux on 2007-05-30
ha forgot the:
$sudo update-rc.d fail2band defaults

much better now. 

hope that will help someone esle.

---

### Post by brigux on 2008-04-29
yep, me again, one year after.. thank you me from one year ago.

---

