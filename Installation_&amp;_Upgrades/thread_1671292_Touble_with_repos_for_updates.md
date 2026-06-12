---
title: "Touble with repos for updates"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by alvinmoneypit on 2011-01-19
Last week, I started having problems with 'Update Manager'.  It gave error stating, "failed to download repository information".  I thought it might be system wide so I awaited a fix, but none was forthcoming, so I posted here.  I have no idea how to fix, maybe reinstall the update manager package??  Below are the details. ```
W:Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/Release.gpg  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/source/Sources.gz  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
, W:Failed to fetch http://pacakge.ubuntu.com/ubuntu/dists/maverick/main/binary-i386/Packages.gz  Something wicked happened resolving 'pacakge.ubuntu.com:http' (-5 - No address associated with hostname)
, E:Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by papibe on 2011-01-19
It seems that either your sources got corrupted, or that server went down. I tried to resolve pacakge.ubuntu.com with no luck:

```
$ nslookup
Default Server:  home
Address:  192.168.1.254

> pacakge.ubuntu.com
Server:  home
Address:  192.168.1.254

*** home can't find pacakge.ubuntu.com: Non-existent domain

```

I don't known if that server doesn't exist or the Domain Name Server for that name is down.

What you can do is to change your sources for a set that is up and working. Check the section "Download Server" on this [page]("https://help.ubuntu.com/community/Repositories/Ubuntu") (Other -> Best Server). It takes a few minutes to determine which one is closer, but it's worth it.

I hope it helps.

---

### Post by alvinmoneypit on 2011-01-19
I changed servers as you suggested.  I went from 'server for the United States' to "server at mit.edu'.  It has the same errors.

Could this have been caused by some downloads I've been installing?  I tried to install some software to make a modem work - some of it is pretty old, circa 2003.  These might be requesting some stuff that  no longer exists maybe??

---

### Post by alvinmoneypit on 2011-01-20
I tried a solution I found on another thread where network manager is modified to enable some DNS features.  I tried one of the solutions and it had no effect. 
 The other would require me to sign up for some service that would enable DNS support.  I'm not going that route right now as this just started happening on a previously working system.

---

### Post by papibe on 2011-01-20
You don't need to subscribe to get a better DNS service. Try Google Open DNS or OpenDNS (works without subscription, although it gets better if you subscribe).

Any way, I'm getting the impression that something happened to your sources because the server package.ubuntu.com seems to not exist. Could you post the content of /etc/apt/sources.list, and the list and content of /etc/apt/sources.list.d/ 

Regards.

---

### Post by papibe on 2011-01-20
You don't need to subscribe to get a better DNS service. Try Google Open DNS or OpenDNS (works without subscription, although it gets better if you subscribe).

Any way, I'm getting the impression that something happened to your sources because the server package.ubuntu.com seems to not exist. Could you post the content of /etc/apt/sources.list, and the list and content of /etc/apt/sources.list.d/ 

Regards.

---

### Post by alvinmoneypit on 2011-01-20
thanks, papibe for helping me with this.  If you want to see the content of the individual files I can post them as well.  I'm downloading updates from mit.edu and have the cd-rom unchecked.


Al

---

