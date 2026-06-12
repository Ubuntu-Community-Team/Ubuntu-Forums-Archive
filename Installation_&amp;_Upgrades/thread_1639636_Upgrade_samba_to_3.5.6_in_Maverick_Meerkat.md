---
title: "Upgrade samba to 3.5.6 in Maverick Meerkat"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by hurricanehrndz on 2010-12-06
Hi,

I was wondering if someone could help how I would go about upgrading samba in Maverick Meerkat, to fix the windows live sign-in assistant? Current stable repositories only supply 3.5.4 for Maverick Meerkat.

Thanks!

---

### Post by dc_williamson on 2010-12-13
Hello

Don't know how you can do it using Synaptic (as I don't think 3.5.6 has been packaged on Launchpad) but you can do it manually - remove old, download, compile, install.

Remove old SAMBA (sudo apt-get --purge remove samba)
Download the new package from samba.org
Extract it (tar xvf samba-3.5.6.tar.gz)
cd samba-3.5.6/source3
sudo ./configure
sudo make
sudo make install

In fact, that's exactly what I'm doing now but on Lucid :)

Remember to backup and config files first, in case they get deleted or over-written.

---

### Post by bhold on 2010-12-28
Anyone care to post the results of their upgrade to samba 3.5.6? 

I downloaded the .gz file for 3.5.6 but have a few questions before I proceed. 

Will the procedure described by dc_williamson install both samba and smbclient?

If the old smbclient must be removed prior to installation of the new, will that cause problems? (synaptic says smbclient is a dependency of ubuntu-desktop).

My system is Ubuntu 10.04 desktop.

---

