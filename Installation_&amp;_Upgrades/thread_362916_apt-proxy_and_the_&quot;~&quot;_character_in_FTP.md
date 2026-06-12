---
title: "apt-proxy and the &quot;~&quot; character in FTP"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by supermihi on 2007-02-16
Hi,

I try to set up apt-proxy to serve our ubuntu computers here with updates without producing to much load / traffic on the update servers.
Everything seems to work fine, but there's one problem: deb files from the "backports"-Repositories always seem to have tilde characters in them (like debootstrap_0.3.3.0ubuntu~edgy1_all.deb), and apt-proxy does some mess when trying to fetch such a package from the outside server.

Update: By typing this I figured out that when I try to access the outside server via http:// instead of ftp:// it works. So it might be a problem with apt-proxy's ftp implementation, or could it even be a misconfigured outside update server? (it's ftp.uni-kl.de/pub/linux/ubuntu, accessible both via ftp and http).

---

