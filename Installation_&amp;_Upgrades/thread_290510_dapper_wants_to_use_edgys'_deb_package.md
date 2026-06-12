---
title: "dapper wants to use edgys' deb package"
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by mwerlberger on 2006-11-01
Hi!

I have a Ubuntu 6.06 Server and want to stick to Dapper for some time because i'm very pleased with most of the packages. Although there are some debs i would like to have from edgy. Or better say the version. In my case this is especially egroupware. In Dapper 1.0.x in Edgy 1.2.x which would be perfekt. Is there an elegant way of integrating single packages from the edgy repositories or do i have to download them and just install with dpkg? Also an installation from source would be ok, but i just want to know how the recommended workflow is for such a "problem" that won't cause any troubles with future updates.

Kind regards,
 Manuel

---

### Post by tribaal on 2006-11-01
Well as far as egroupware goes, why don't you just download the php files from [www.egroupware.com](www.egroupware.com) and then unzip it in a directory under your webroot?
The "install script" is a php script anyway, and all the config is web-based...

Anyway, if you want to use debs that are more up-to-date, you might want to uncomment the "backports" repository in your /etc/apt/sources.list, or otherwise download the debs from the web and use dpkg -i.

If you consider upgrading to Edgy, I strongly suggest you do so with a fresh install, as the upgrade process is pretty error prone.

Hope this helps...

- trib'

---

### Post by mwerlberger on 2006-11-01
> **tribaal said:**
> Well as far as egroupware goes, why don't you just download the php files from [www.egroupware.com](www.egroupware.com) and then unzip it in a directory under your webroot?
The "install script" is a php script anyway, and all the config is web-based...


Of course with egroupware it isn't that big deal. I just wanted to know if there is a proper way to stick to Dapper and use some (only for certain apps) debs from the Edgy repositories.

> **tribaal said:**
> 
Anyway, if you want to use debs that are more up-to-date, you might want to uncomment the "backports" repository in your /etc/apt/sources.list, or otherwise download the debs from the web and use dpkg -i.


ok the thing with deb download and installation is clear...

> **tribaal said:**
> 
If you consider upgrading to Edgy, I strongly suggest you do so with a fresh install, as the upgrade process is pretty error prone.


No. Don't want to update. Just screwed my Desktop with an upgrade. Do not want to screw up my server. Maybe the people using it for Mail won't be that happy :rolleyes: .

Thanks for your reply. Concerning egroupware i will stick to the manual installation. Sounds like the best way of doing it.

Rgds,
 Manuel

---

