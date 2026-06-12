---
title: "Installing and getting updates via proxy server"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by Annorax on 2011-10-19
Hi all,

I'm trying to install Ubuntu 11.10. My computer is connected to the internet via a proxy server. I would like that during the install, any updates can be downloaded and applied, but the installer tells me I am not on the internet as I have not set the proxy. How can I set the proxy before the installation?

---

### Post by haqking on 2011-10-19
> **Annorax said:**
> Hi all,

I'm trying to install Ubuntu 11.10. My computer is connected to the internet via a proxy server. I would like that during the install, any updates can be downloaded and applied, but the installer tells me I am not on the internet as I have not set the proxy. How can I set the proxy before the installation?

Depends how you are installing.

If you are using a Live CD medium you probably need to make a custom one as apt is not set to use a proxy by default.

Why not install and then update ?

Also your net admin or whoever needs to allow it as it may not necessarily go through the proxy anyways.

---

### Post by Annorax on 2011-10-19
I am using the Live CD. What I typically do is the install and then update, but I was wondering if there was a way to do it all at once through a proxy. But I guess not. :)

---

### Post by haqking on 2011-10-19
> **Annorax said:**
> I am using the Live CD. What I typically do is the install and then update, but I was wondering if there was a way to do it all at once through a proxy. But I guess not. :)

Well you can make a custom live install [https://help.ubuntu.com/community/LiveCDCustomization](https://help.ubuntu.com/community/LiveCDCustomization) or make a USB and modify that

and see here [http://askubuntu.com/questions/26584/using-an-apt-proxy-for-downloads-during-installation](http://askubuntu.com/questions/26584/using-an-apt-proxy-for-downloads-during-installation)

---

