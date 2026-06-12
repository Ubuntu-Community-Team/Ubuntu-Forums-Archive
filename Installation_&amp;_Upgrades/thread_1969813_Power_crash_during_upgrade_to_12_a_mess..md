---
title: "Power crash during upgrade to 12 a mess."
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by TorMike on 2012-04-30
Upgrading to v 12 from the power crashed.

When the power returned Ubuntu came up but when I tried to continue the install I keep getting a message box

[B]"Not All updates can be installed"  
Run a partial upgrade, to install as many updates as possible.
[/B]
So I clicked on 'Partial Upgrade' and I immediated get the error message:

[B]"Can Not Upgrade"  
An upgrade from 'precise' to 'oneiric' is not supported with this tool[/B].

OK, how do I get aroung this issue???

---

### Post by nashibuntu on 2012-04-30
After a crashed upgrade which forced me to reboot the following saved me by completing the upgrade:

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get -f install
```

Maybe the same will work for you.

---

### Post by TorMike on 2012-05-01
Nope.

Still get the same error messages

---

### Post by TorMike on 2012-05-01
Well, I think I fixed it.

I used this link to help me.


**[http://www.liberiangeek.net/2011/10/how-to-upgrade-to-ubuntu-11-10-oneiric-ocelot-from-ubuntu-11-04-natty-narwhal-via-the-console-server/](http://www.liberiangeek.net/2011/10/how-to-upgrade-to-ubuntu-11-10-oneiric-ocelot-from-ubuntu-11-04-natty-narwhal-via-the-console-server/)**

Once I reinstalled/upgraded the manager file I was able to successfuly run the 'Partial Upgrade'.

And now I'm running v12.

---

