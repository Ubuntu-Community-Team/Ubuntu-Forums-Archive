---
title: "Proxy prevents installation of msttcorefonts package"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by rickbeton on 2008-05-01
Hi,

I'm happily using Ubuntu8.04 on a LAN and my network proxy settings allow access to the 'Net. Synaptic works fine except that it cannot install msttcorefonts. There is a post-install script that wants to fetch files from the 'Net but doesn't use the proxy to do so. So it fails.

Is there a way to do this manually using dpkg etc?

Rick

---

### Post by rickbeton on 2008-05-06
No-one answered my question but I found a solution on the web:

[http://www.nabble.com/Installing-the-msttcorefonts-package-on-a-mchine-withou-internet-access-td15501534.html](http://www.nabble.com/Installing-the-msttcorefonts-package-on-a-mchine-withou-internet-access-td15501534.html)

Also:
[https://answers.launchpad.net/ubuntu/+question/15835](https://answers.launchpad.net/ubuntu/+question/15835)
[http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/](http://ubuntu.wordpress.com/2005/09/09/installing-microsoft-fonts/)

---

### Post by cubabit on 2011-01-26
Another solution is to run:

```
sudo dpkg-reconfigure ttf-mscorefonts-installer
```

As this starts a text based installer that gives you the option to supply a proxy configuration

---

