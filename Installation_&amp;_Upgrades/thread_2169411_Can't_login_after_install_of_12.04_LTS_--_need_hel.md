---
title: "Can't login after install of 12.04 LTS -- need help!"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by Ari_Passopolis on 2013-08-22
I installed 12.04 over a less stable version. The resulting system would not boot. I  used the Boot-Repair tool (see results at [http://paste.ubuntu.com/6012606/](http://paste.ubuntu.com/6012606/)). The system now boots  but the login process is an infinite loop. I login, the screen darkens, and I get the same login prompt all over again. Big time thanks to anyone who can help me access my data, which I keep in a separate partition (\=sda1 and \home=sda5). I'm completely  out of ideas!

---

### Post by Ari_Passopolis on 2013-08-22
An additional piece of info: I *am able* to login from the recovery command line. Helpful ideas, hints and thoughts are most welcome.

---

### Post by steeldriver on 2013-08-22
Did you reuse your original home directory? if so check its ownership and permissions are correct

```
ls -l /home
```

Also check permissions on your .Xauthority and .ICEauthority files

 ```
ls -l /home/*user*/.{ICE,X}authority
```

where *user* is your actual login name

---

### Post by Ari_Passopolis on 2013-08-22
Bingo! I lacked write permission to my home folder. Thanks so much for  helping-you saved my ass and my sanity.

---

