---
title: "Could not reliably determine the server's fully qualified domain name?"
date: 2015-06-28
forum: Installation &amp; Upgrades
---

### Post by Jim_Dodds on 2015-06-28
I get that error and googled it and it says to use gedit to fix the server name. In putty I can't open up gedit I downloaded it and says warning unable to open ??? How do I fix this error? I'm not running a virtual machine.

---

### Post by steeldriver on 2015-06-28
Hello and welcome to the forums

The editor that you use doesn't have to be gedit: if you're connected via putty then use a CLI editor. The default in Ubuntu is called `nano`

```

sudo nano /etc/apache2/conf-available/fqdn.conf

```

FWIW the message is only a warning - apache2 should start and function fine without a fqdn

---

### Post by Jim_Dodds on 2015-06-28
It gives me error no such file or directory? So it will be fine your saying until I get my website up and running?

---

