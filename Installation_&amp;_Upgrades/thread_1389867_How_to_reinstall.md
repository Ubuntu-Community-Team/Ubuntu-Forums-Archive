---
title: "How to reinstall"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by thejinx0r on 2010-01-24
How can I reinstall a package, including the conf files?

So here;s my problem.
I purged samba from my server using "apt-get purge".
Then, I noticed some conf files left over in /etc/samba so I deleted those.

Now when I run "apt-get install samba" the conf files aren't replaced and samba fails to load. 

So, how can I get apt-get to reinstall (restore) them?

Thank yoo.

---

### Post by Barriehie on 2010-01-24
> **thejinx0r said:**
> How can I reinstall a package, including the conf files?

So here;s my problem.
I purged samba from my server using "apt-get purge".
Then, I noticed some conf files left over in /etc/samba so I deleted those.

Now when I run "apt-get install samba" the conf files aren't replaced and samba fails to load. 

So, how can I get apt-get to reinstall (restore) them?

Thank yoo.

Try apt-get --reinstall 

Barrie

---

### Post by thejinx0r on 2010-01-25
So I tried that already, and it didn't work.

So to be even more thorough, here's a list of thing I tried:

apt-get purge then install samba;
apt-get install --reinstall samba;
dpkg -r samba; then apt-get install;
dpkg-reconfigure samba;

more too, but, can't really remember all of them of the of my head.

But more suggestions would be welcomed.

---

### Post by Barriehie on 2010-01-25
You can try using dpkg to install it.  I'ld first look in the file **/var/lib/dpkg/status** and search it for samba, if found I'ld delete that section and then:
```
dpkg -i samba
```
all this of course AFTER making a backup copy of the status file.

Barrie

---

