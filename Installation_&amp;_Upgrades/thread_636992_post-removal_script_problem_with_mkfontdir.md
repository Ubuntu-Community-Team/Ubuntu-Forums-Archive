---
title: "post-removal script problem with mkfontdir"
date: 2007-12-10
forum: Installation &amp; Upgrades
---

### Post by bistros on 2007-12-10
Hi all:

I'm having a post-removal script problem with xfonts-scalable where the update-fonts-dir script is returning an error condition that causes apt-get -f install to fail.  I've tried apt-get update, apt-get upgrade, dpkg -r -force-remove-reinstreq xfonts-scalable .....

I need to get this system working again, and it will not proceed with the upgrade from dapper to fiesty until I   get past this error.

It appears the post-removal script has an error in it that causes this failure - if I could get to the script, I'd try to fix it myself.

---

### Post by bistros on 2007-12-10
Fixed

I installed xfonts-utils and this allowed the script in the package to run properly.

---

