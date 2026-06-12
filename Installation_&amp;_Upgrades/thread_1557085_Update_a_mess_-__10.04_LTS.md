---
title: "Update a mess -  10.04 LTS"
date: 2010-08-20
forum: Installation &amp; Upgrades
---

### Post by fidgaf on 2010-08-20
I'm running Update Manager and getting:

> Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?

I usually say no but have now gone for Yes and then get this:

> W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-23.37_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_2.6.32-23.37_i386.deb)
  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.11-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/freetype/libfreetype6_2.3.11-1ubuntu2.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgp11-0_2.92.92.is.2.30.3-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgp11-0_2.92.92.is.2.30.3-0ubuntu1_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgcr0_2.92.92.is.2.30.3-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libgcr0_2.92.92.is.2.30.3-0ubuntu1_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_2.92.92.is.2.30.3-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/gnome-keyring_2.92.92.is.2.30.3-0ubuntu1_i386.deb)
  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_3.6.6+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.0_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.0_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.0-gnome-support_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.0-gnome-support_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.5_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.5_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.5-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb](http://security.ubuntu.com/ubuntu/pool/universe/f/firefox/firefox-3.5-branding_3.6.6+nobinonly-0ubuntu0.10.04.1_all.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.1.53.64ubuntu0.10.04.3_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.10.04.3_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_10.1.53.64ubuntu0.10.04.3_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gdm/gdm_2.30.2.is.2.30.0-0ubuntu2_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_2.92.92.is.2.30.3-0ubuntu1_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/g/gnome-keyring/libpam-gnome-keyring_2.92.92.is.2.30.3-0ubuntu1_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.23.24_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_2.6.32.23.24_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.23.24_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_2.6.32.23.24_i386.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.23.24_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_2.6.32.23.24_i386.deb)
  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.5+build2+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_3.0.5+build2+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.2_all.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-common_1.7.6-2ubuntu7.2_all.deb)
  404  Not Found


W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.2_i386.deb](http://gb.archive.ubuntu.com/ubuntu/pool/main/x/xorg-server/xserver-xorg-core_1.7.6-2ubuntu7.2_i386.deb)
  404  Not Found


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.6+nobinonly-0ubuntu0.10.04.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/x/xulrunner-1.9.2/xulrunner-1.9.2_1.9.2.6+nobinonly-0ubuntu0.10.04.1_i386.deb)
  404  Not Found [IP: 91.189.88.37 80]





Current system says "10.04 LTS" - This may or may not be true, false or partly true (or false). :)

How do I get it to install all updates?

Thanks

---

### Post by kansasnoob on 2010-08-20
I'm curious what server you're using?

Is "gb" Great Britain?

Maybe try a different server, like "uk" or "main". You can change it in System > Admin > Software Sources.

If that does no good, please post the output of these two commands from terminal:

```
cat /etc/apt/sources.list
```

```
ls /etc/apt/sources.list.d
```

---

### Post by fidgaf on 2010-08-20
Switching to Main seems to have solved the problem and all seemed to install.

Afterwards I switched to UK server. there were some failed files but no error messages.

I'll keep an eye on it but all works for now.

Thanks.

---

