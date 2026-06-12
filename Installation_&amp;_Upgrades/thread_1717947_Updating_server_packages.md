---
title: "Updating server packages"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by yakatz on 2011-03-30
I am running Ubuntu 10.04 LTS with Apache 2.2.14 and apache2-mpm-itk (2.2.14-5ubuntu8.4) (both installed from apt-get).

I saw that there are updates to the MPM-ITK package. 

If I understand the packages website correctly, the new version is in the repository for natty ([link]("http://packages.ubuntu.com/search?searchon=names&keywords=mpm-itk"))

This server was built using a deploy script from Linode ([link]("http://www.linode.com/stackscripts/view/?StackScriptID=10")).

The server is also not heavily used right now so I could upgrade to 10.10 (I do not want to wait until 11.10 for an LTS release).
(Aside: am I wrong to want to wait for an LTS release?)

---

### Post by Enigmapond on 2011-03-30
No I ONLY do LTS's as they seem to be the most stable. Regarding the package, the version you want can be downloaded in a deb file right from here:
[https://launchpad.net/ubuntu/lucid/amd64/apache2-mpm-itk/2.2.14-5ubuntu8](https://launchpad.net/ubuntu/lucid/amd64/apache2-mpm-itk/2.2.14-5ubuntu8)

---

### Post by yakatz on 2011-03-30
> **Enigmapond said:**
> No I ONLY do LTS's as they seem to be the most stable. Regarding the package, the version you want can be downloaded in a deb file right from here:
[https://launchpad.net/ubuntu/lucid/amd64/apache2-mpm-itk/2.2.14-5ubuntu8](https://launchpad.net/ubuntu/lucid/amd64/apache2-mpm-itk/2.2.14-5ubuntu8)

If it is available there, shouldn't it be available when I run ```
apt-get update; apt-get upgrade
```?

(I was always told to stay with the package manager whenever possible because it will keep track of all the dependencies. (Well that is the theory))

---

