---
title: "Edgy Upgrade Issue (37 Packages waiting to be upgraded, but don't upgrade)"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by NickPresta on 2006-10-27
It shouldn't make a difference but I'm on Kubuntu 6.10 EE.
My upgrade to Edgy went well - no X, kdm, etc problems. However, now I get Adept saying that there are 37 packages to be updated. The little icon loads up each time I start up the computer. I follow procedure and go through the whole process to upgrade. It says it went fine, Goodbye.

However, these new packages aren't upgraded and when I do a `sudo apt-get dist-upgrade`, I have those 37 packages, but they are being held back/won't upgrade.

Here are the packages:
```
me@mysystem:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  hpijs libggi2 mplayer python-adns python-clientcookie python-crypto python-dnspython python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-gadfly python-glade2 python-gnome2 python-gtk2 python-htmlgen python-htmltmpl
  python-imaging python-imaging-sane python-jabber python-kjbuckets python-ldap python-mysqldb python-pam python-pexpect python-pgsql
  python-pylibacl python-pyopenssl python-pyorbit python-pyxattr python-reportlab python-simpletal python-soappy python-sqlite python-syck
  python-xml python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 37 not upgraded.
```

When I do a `sudo apt-get update`, I get this:

```
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/edgy/Release.gpg Read error - read (104 Connection reset by peer)
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/edgy/main/i18n/Translation-en_CA.bz2 Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/edgy/Release
Failed to fetch http://kubuntu.org/packages/amarok-latest/dists/edgy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch ftp://cipherfunk.org/pub/packages/ubuntu/dists/edgy/main/binary-i386/Packages.gz Could not connect to cipherfunk.org:21 (205.178.189.131), connection timed out

```

Which is fine, right? Python packages aren't from cipherfunk.org, IIRC.


Any suggestions? I don't want a stupid Adept icon telling me there are 37 packages to upgrade every time I start the computer.

---

### Post by nyinge on 2006-10-27
Check [this page]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade") out on apt-get on Debian website.

---

### Post by vibestriton on 2006-10-27
There is no edgy amarok release here...  
[http://kubuntu.org/packages/amarok-latest/dists/](http://kubuntu.org/packages/amarok-latest/dists/)
Comment it out of /etc/apt/sources.list with "#".


There is no edgy wine release here...
[http://wine.budgetdedicated.com/apt/dists/](http://wine.budgetdedicated.com/apt/dists/)
Comment it out of /etc/apt/sources.list with "#".

cipherfunk.org seems to be down at the moment...
You might want to comment that out too (until? it comes back).

---

### Post by Gaute65 on 2006-10-28
> **nyinge said:**
> Check [this page]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade") out on apt-get on Debian website.

I had the same problem as OP, Thanks for the help. :)

---

### Post by NickPresta on 2006-10-29
> **nyinge said:**
> Check [this page]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-dist-upgrade") out on apt-get on Debian website.

Thank you, sir.

Thank you to everyone else too.

---

