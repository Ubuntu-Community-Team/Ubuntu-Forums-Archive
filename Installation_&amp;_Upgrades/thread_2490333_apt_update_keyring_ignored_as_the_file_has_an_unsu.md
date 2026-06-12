---
title: "apt update keyring ignored as the file has an unsupported filetype"
date: 2023-08-30
forum: Installation &amp; Upgrades
---

### Post by lofftjm2 on 2023-08-30
$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.3 LTS
Release:	22.04
Codename:	jammy


$ sudo apt update
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-backports InRelease
Hit:4 [https://downloads.plex.tv/repo/deb](https://downloads.plex.tv/repo/deb) public InRelease
Hit:5 [http://as-repository.openvpn.net/as/debian](http://as-repository.openvpn.net/as/debian) jammy InRelease
Hit:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-security InRelease
Hit:7 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
1 package can be upgraded. Run 'apt list --upgradable' to see it.
W: [http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/jammy/InRelease:)              The key(s) in the keyring /etc/apt/trusted.gpg.d/as-repo-public.gpg are ignored as the file has an unsupported filetype.
W: [http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/jammy-updates/InRelease:)      The key(s) in the keyring /etc/apt/trusted.gpg.d/as-repo-public.gpg are ignored as the file has an unsupported filetype.
W: [http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/jammy-backports/InRelease:)    The key(s) in the keyring /etc/apt/trusted.gpg.d/as-repo-public.gpg are ignored as the file has an unsupported filetype.
W: [http://us.archive.ubuntu.com/ubuntu/dists/jammy-security/InRelease:](http://us.archive.ubuntu.com/ubuntu/dists/jammy-security/InRelease:)     The key(s) in the keyring /etc/apt/trusted.gpg.d/as-repo-public.gpg are ignored as the file has an unsupported filetype.
W: [https://dl.google.com/linux/chrome/deb/dists/stable/InRelease:](https://dl.google.com/linux/chrome/deb/dists/stable/InRelease:)          The key(s) in the keyring /etc/apt/trusted.gpg.d/as-repo-public.gpg are ignored as the file has an unsupported filetype.


$ file /etc/apt/trusted.gpg.d/as-repo-public.gpg
/etc/apt/trusted.gpg.d/as-repo-public.gpg: PGP public key block Public-Key (old)



Any ideas on how to correct the issue would be greatly appreciated.

---

### Post by #&amp;thj^% on 2023-08-30
Well that looks fun, can you show us this:
```
***cd /etc/apt/trusted.gpg.d/ && ls**
google-chrome.gpg            trusted.gpg
mozillateam-ubuntu-ppa.gpg   ubuntuhandbook1-ubuntu-conkymanager2.gpg
mozillateam-ubuntu-ppa.gpg~  ubuntuhandbook1-ubuntu-conkymanager2.gpg~
skypeforlinux.gpg            ubuntu-keyring-2012-cdimage.gpg
surfshark.asc                ubuntu-keyring-2018-archive.gpg
teamviewer.gpg

```

---

### Post by lofftjm2 on 2023-08-31
$ cd /etc/apt/trusted.gpg.d/ && ls
as-repo-public.gpg  as-repository.asc  google-chrome.gpg  ubuntu-keyring-2012-cdimage.gpg  ubuntu-keyring-2018-archive.gpg

I think the as-* ones are related to openvpn.  I will look into that in the meantime.

---

### Post by #&amp;thj^% on 2023-08-31
> **lofftjm2 said:**
> 
I think the as-* ones are related to openvpn.  I will look into that in the meantime.
That would be great, and in the meantime show this as well please:
```
sudo apt-key --keyring /etc/apt/trusted.gpg list

```

---

### Post by lofftjm2 on 2023-08-31
$ sudo apt-key --keyring /etc/apt/trusted.gpg list
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
/etc/apt/trusted.gpg
--------------------
pub   rsa4096 2015-03-22 [SC]
      CD66 5CBA 0E2F 88B7 373F  7CB9 9720 3C7B 3ADC A79D
uid           [ unknown] Plex Inc.
sub   rsa4096 2015-03-22 [E]


pub   rsa4096 2019-03-15 [SC]
      8B1B C7FE CB72 59E1 430A  3AA0 26EB 3912 3AAA AA96
uid           [ unknown] Access Server (Access Server Package Key) <packaging@openvpn.net>
sub   rsa4096 2019-03-15 [E]



OpenVPN support had me remove the as-repo-public.gpg file and now apt update does not produce any warnings.

---

### Post by #&amp;thj^% on 2023-08-31
Nice and thanks for reporting back, it did show the bad file:
```
pub rsa4096 2015-03-22 [SC]
CD66 5CBA 0E2F 88B7 373F 7CB9 9720 3C7B 3ADC A79D
uid [ unknown] Plex Inc.
sub rsa4096 2015-03-22 [E]


pub rsa4096 2019-03-15 [SC]
8B1B C7FE CB72 59E1 430A 3AA0 26EB 3912 3AAA AA96
uid [ unknown] Access Server (Access Server Package Key) <packaging@openvpn.net>
sub rsa4096 2019-03-15 [E]
```

---

