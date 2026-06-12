---
title: "Failed to fetch some files during upgrade to 7.04"
date: 2007-05-22
forum: Installation &amp; Upgrades
---

### Post by g0m3z78 on 2007-05-22
Hi,

I'm experiencing the following error message when trying to upgrade from 6.10 to 7.04:

Failed to fetch [http://www.beerorkid.com/compiz/dists/edgy/Release.gpg](http://www.beerorkid.com/compiz/dists/edgy/Release.gpg) The HTTP server sent an invalid reply header 
Failed to fetch [http://www.beerorkid.com/compiz/dists/edgy/main-edgy/i18n/Translation-en_AU.bz2](http://www.beerorkid.com/compiz/dists/edgy/main-edgy/i18n/Translation-en_AU.bz2) Bad header line 
Failed to fetch [http://www.beerorkid.com/compiz/dists/edgy/main-edgy/binary-i386/Packages.gz](http://www.beerorkid.com/compiz/dists/edgy/main-edgy/binary-i386/Packages.gz) Bad header line

I'm getting the same even if I want to upgrade through the console by typing:

gksu "update-manager -c"

Do I need to modify my source.list to download packages from other server? Can somebody help me out on this?

Thanks in advance,
g0m3z78

---

### Post by pxwpxw on 2007-05-22
post your sources.list.
browse to that site, what is it?
does the upgrade continue or abort?

---

### Post by g0m3z78 on 2007-05-22
Unfortunately I'm not at my PC at the moment, so I'll post my source.list sometimes afternoon. I have already browsed the site. It's a community portal with some funny videos, pictures and some blog. The upgarde aborts after the message pops up and I click on close button.

Thanks,
g0m3z78

---

### Post by pxwpxw on 2007-05-22
OK, will check later. But if you have not downloaded from that site, and its not in your sources.list it should not be happening. Maybe there is a plugin in your browser or other aplliction that is trying to update, but it is certainly not a ubuntu repository and should not be part of the upgrade.

---

### Post by g0m3z78 on 2007-05-22
Thanks. But how can it happen? I mean what is the logic behind the upgrade? If I click on the upgrade button on the upgrade-manager why the system checks other so called "unofficial" repositories? Sorry I'm using Ubuntu since November/2006 only.

Thanks once again,
g0m3z78

---

### Post by g0m3z78 on 2007-05-22
I have checked content of my source.list and found one link to previously mentioned site. I can remember that I put it there when I tried to install Beryl. It was few months back. After I commented out this row upgrade started successfully. It was my mistake. Upgrade is currently running. Sorry for inconveniences.

Issue closed...

Many thanks for your prompt action PXW

Kind regards,
g0m3z78

---

### Post by beerorkid on 2007-05-22
Sorry about that.  There are thousands of dead links out there.
I finally killed the repo cuz of some issues I was having with my webhost.  And it had not been updated since last november.  So really out of date.

check [opencomposting]("http://www.opencompositing.org/") for new install guides.

There were no feisty packages there anyways.

I edited my .htaccess to completely block the 1.5 million hits a month that were going to my old 404.php  (since they were looking for packages that did not exist, even when the repo was up)  It was sucking up some huge CPU minutes on my shared hosting.

---

### Post by g0m3z78 on 2007-05-23
Good news! Thus others won't face the same problem at least. Thanks for your post beerorkid!

Regards,
g0m3z78

---

