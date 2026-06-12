---
title: "apt-get update not working on 9.1"
date: 2011-04-26
forum: Installation &amp; Upgrades
---

### Post by baker626 on 2011-04-26
Hi All,

New to Ubuntu and for some reason, I'm not able to get apt-get update to run correctly on a newly installed server. I keep getting multiple failures all similar to the following:

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/karmic-security/universe/i18n/Translation-en_US.bz2 Unable to connect to security.ubuntu.com http: [IP: 91.189.92.167 80]

I'm running Ubuntu 9.1 and have it as a guest in VMWare 2.0 on a windows machine. I'm able to ping other sites - so I'm pretty sure it's not a network configuration issue.

Any help at all would be appreciated.

Thanks,
Avi

---

### Post by Dutch70 on 2011-04-26
Hi and welcome to UF

You can try choosing a different mirror if you want, but I believe 9.10 Karmic Koala reaches it's EOL (End Of Life) in 3 days (April 29th). I think that is for the desktop or server since it's not an LTS.
[[COLOR="Red"]http://en.wikipedia.org/wiki/List_of_Ubuntu_releases[/COLOR]]("http://en.wikipedia.org/wiki/List_of_Ubuntu_releases")



You should consider installing 10.04 LTS (Long Term Support) which is supported for 5 years on the server side & 3 years on the desktop side. That is from April 2010, hence the 10.04 name.

If you're not concerned about long term support, then you can try 10.10 Maverick Meerkat.
11.04 Natty Narwhal will be officially released on April 28th, but will probably be buggy for a while.

---

