---
title: "upgrade from 11.1- to 12.04 alternate using cdrom FAILED"
date: 2012-05-31
forum: Installation &amp; Upgrades
---

### Post by LinuxGold on 2012-05-31
Currently running Ubuntu 11.10 desktop, 64 bits into my laptop
running on Intel Core i5-2410M CPU @ 2.30GHz x 4

Downloaded ubuntu-12.04-alternate-amd64.iso file

shut down network to prevent cdromupgrade from retrieving files online:

ifconfig eth0 down
ifconfig wlan1 down

ran cdromupgrade, brought up graphical interface to install update to 12.04, 
declined "latest updates from the Internet" option,
Failed at "Getting new packages" with the following error:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-core_3.5.3-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-core_3.5.3-0ubuntu1_amd64.deb) Could not resolve 'wwwproxy.k12.de.us'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-common_3.5.3-0ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libr/libreoffice/libreoffice-common_3.5.3-0ubuntu1_all.deb) Could not resolve 'wwwproxy.k12.de.us'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_18.0.1025.151~r130497-0ubuntu1_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/c/chromium-browser/chromium-browser_18.0.1025.151~r130497-0ubuntu1_amd64.deb) Could not resolve 'wwwproxy.k12.de.us'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-24-generic_3.2.0-24.39_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-3.2.0-24-generic_3.2.0-24.39_amd64.deb) Could not resolve 'wwwproxy.k12.de.us'

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/f/fonts-unfonts-core/fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/f/fonts-unfonts-core/fonts-unfonts-core_1.0.3.is.1.0.2-080608-5ubuntu1_all.deb) Could not resolve 'wwwproxy.k12.de.us'

closed app
ifconfig eth0 up
ifconfig wlan1 up

reported with error here.  cdromupgrade refused to skip the online check like it should.

How do I bypass this problem?

Thanks.

---

