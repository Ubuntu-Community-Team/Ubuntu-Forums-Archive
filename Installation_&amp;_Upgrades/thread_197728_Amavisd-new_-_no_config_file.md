---
title: "Amavisd-new - no config file?"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by jimwillsher on 2006-06-16
Hi,

I'm doing a clean install of Dapper. I've installed amavisd and clamav via:

apt-get install clamav clamav-daemon amavisd-new

but I don't have an /etc/amavis/amavisd.conf file. Breezy used to install a huge config file which I then tweaked. Am I missing something silly? I can obviously copy the file from Breezy, but it might not be compatible (and at first sight it isn't compatible, as amavisd seems to be doing nothing!)



Jim

PS Installed from the Dapper Server CD.

---

### Post by jimwillsher on 2006-06-16
*bump* 

Anyone?

---

### Post by jimwillsher on 2006-06-16
Okay, I sorted it.

From [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/) :

Changes for Ubuntu 6.06, Dapper Drake
All amavis configurations are in several files in /etc/amavis/conf.d/





Jim

---

