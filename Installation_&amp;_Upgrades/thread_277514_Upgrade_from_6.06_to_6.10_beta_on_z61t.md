---
title: "Upgrade from 6.06 to 6.10 beta on z61t"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by cholguin on 2006-10-14
I am trying to upgrate to 6.10 but was not able to, first i downloaded the iso and burn the CD but the CD crashes when i boot and try to run the live part to install. Second i tried to do an upgrade using the gksu "update-manager -c -d" and downloaded all files needed trough this command to do the upgrade, but the program is not able to download the last 31 (from 908 to 939) files where it states the following:

Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-default_2.0.4~rc3-0ubuntu4_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/openoffice.org-style-default_2.0.4~rc3-0ubuntu4_all.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2_2.1.19.dfsg1-0.2ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2_2.1.19.dfsg1-0.2ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.19.dfsg1-0.2ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/c/cyrus-sasl2/libsasl2-modules_2.1.19.dfsg1-0.2ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1-glib_0.5.4-0ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1-glib_0.5.4-0ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1_0.5.4-0ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/libpoppler1_0.5.4-0ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.5.4-0ubuntu4_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/poppler/poppler-utils_0.5.4-0ubuntu4_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/python-apt/python-apt_0.6.19ubuntu9_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserver1.2-7_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.99+2.0rc2+dfsg-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnspr4_1.firefox1.99+2.0rc2+dfsg-0ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedataserverui1.2-8_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libecal1.2-7_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-12_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libegroupwise1.2-12_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-2_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libexchange-storage1.2-2_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-book1.2-2_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libedata-cal1.2-6_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.8.1-0ubuntu3_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/evolution-data-server-common_1.8.1-0ubuntu3_all.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.99+2.0rc2+dfsg-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/libnss3_1.firefox1.99+2.0rc2+dfsg-0ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libcamel1.2-8_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.8.1-0ubuntu3_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/e/evolution-data-server/libebook1.2-9_1.8.1-0ubuntu3_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.99+2.0rc2+dfsg-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_1.99+2.0rc2+dfsg-0ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.99+2.0rc2+dfsg-0ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_1.99+2.0rc2+dfsg-0ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea4_3.0-17ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/t/tetex-bin/libkpathsea4_3.0-17ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/devmapper/libdevmapper1.02_1.02.07-1ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/devmapper/libdevmapper1.02_1.02.07-1ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux-locales_2.12r-11ubuntu2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux-locales_2.12r-11ubuntu2_all.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.12r-11ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/mount_2.12r-11ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.12r-11ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/util-linux_2.12r-11ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/u/util-linux/bsdutils_2.12r-11ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext-base_0.15-2ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext-base_0.15-2ubuntu1_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2_all.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/p/popularity-contest/popularity-contest_1.33ubuntu2_all.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/d/devmapper/dmsetup_1.02.07-1ubuntu2_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/d/devmapper/dmsetup_1.02.07-1ubuntu2_i386.deb) 404 Not Found
Failed to fetch [http://au.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.15-2ubuntu1_i386.deb](http://au.archive.ubuntu.com/ubuntu/pool/main/g/gettext/gettext_0.15-2ubuntu1_i386.deb) 404 Not Found

Please help i dont know what else to do.

God bless:cry:

---

### Post by killhup on 2006-10-16
Stupid question, but have you tried "sudo" in front of gksu "update-manager -c -d"?

---

### Post by cholguin on 2006-10-16
Actually i logged in as root so it was not necessary, when i intend to do large changes on my system i tend to log in as root.

God bless. 

Please help with this problem, or will i have to wait for the final release, if so can anyone tell me when this is happening in october?? ](*,) 

God bless.

---

### Post by ocertain on 2006-10-16
I'm a ubuntu newbie, so you might want to take this with a grain of salt. I had installed 6.10 on a laptop but had to wipe it and go down to 6.06. From what I've seen 6.10 is still a bit buggie. It would not allow me to install Java SE which I have to have. The 6.06 Java install went flawlessly and I coded a test app within a few minutes of the installation. 

Personally, unless I had a tangible need to move to 6.10 I'd stick with 6.06.

---

### Post by spier on 2006-10-16
> **killhup said:**
> Stupid question, but have you tried "sudo" in front of gksu "update-manager -c -d"?

Following my stupid tip:
Try removing the "au." mirrorrs... :cool:

---

