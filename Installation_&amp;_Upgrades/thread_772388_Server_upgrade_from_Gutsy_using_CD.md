---
title: "Server upgrade from Gutsy using CD?"
date: 2008-04-28
forum: Installation &amp; Upgrades
---

### Post by richcoosa19 on 2008-04-28
I have a server installation that is currently running Gutsy 7.10.  Is there a way that instead of having the upgrade pull down all packages either via FTP, RSYNC, or HTTP could I perform the upgrade via the install cd?  This would make for a much faster installation and would keep the network from getting bogged down seeing as how I downloaded the Server Install cd over the weekend.  So far the only upgrade path that I have found is to do the 'sudo do-release-upgrade'...

Thanks,
Richie

---

### Post by richcoosa19 on 2008-04-28
Could I just add the cd to the apt sources, do a apt-get update and then a apt-get dist-upgrade?  Or would that break stuff?

---

### Post by richcoosa19 on 2008-04-28
Can I get a bump, bump?

---

### Post by az on 2008-04-28
> **richcoosa19 said:**
> Could I just add the cd to the apt sources, do a apt-get update and then a apt-get dist-upgrade?  Or would that break stuff?

sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade

Keep your online repos active, since you will want up-to-the-minute security updates.  As well, if you have packages installed that are not on the cd, you will need them to be up-to-date or you risk breaking something.  But if the same packages are available locally (on the cd), apt will get them from there instead of the network.

---

### Post by richcoosa19 on 2008-04-29
Thanks!

---

### Post by Stu09 on 2009-02-01
Would this work upgrading from Dapper LTS to Hardy LTS ?

---

