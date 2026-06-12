---
title: "Problem updating Dapper to Edgy (Amd64)"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Macdelaney on 2007-06-07
Hi,
I've been trying to get Edgy going, but i have runned into something i've found nothing about.
After i run ```
gksu "update-manager -c
``` and choose to update to 6.10, i get this message:>  Failed to fetch [http://ubuntu.moshen.de/dists/dapper/Release](http://ubuntu.moshen.de/dists/dapper/Release) Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?) Does anyone has any idea?

---

### Post by arkham on 2007-06-07
Looks like that mirror does not have feisty installed yet, or at least not for your architecture.

Edit /etc/apt/sources.list

Make sure to replace that repository with another (like [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) ) and then run the upgrader again, failing that you can try manually:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by Macdelaney on 2007-06-07
Thanks, i changed it to [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) and it worked!

---

### Post by Enginirical on 2007-06-08
Hey

I'm having smilar problems:(

Can you please remind me what to type in the ATP line when adding the repositiry?

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy ??? I can't find the page that explains it!

Thnks

---

### Post by zvacet on 2007-06-09
```
gksudo gedit /etc/apt/sources.list
```

and put that line there.Save the file.
```
sudo aptitude update
```

---

