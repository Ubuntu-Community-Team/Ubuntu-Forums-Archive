---
title: "problems with apt-get upgrade"
date: 2005-09-25
forum: Installation &amp; Upgrades
---

### Post by Milambar on 2005-09-25
It tried to upgrade mozilla-firefox, and failed with the following error messages.

> Preparing to replace mozilla-firefox 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/var/lib/mozilla-firefox/extensions.d/00classic', which is also in package firefox
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Preparing to replace mozilla-firefox-gnome-support 1.0.6-1ubuntu1~5.04ubp1 (using .../mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb) ...
Unpacking replacement mozilla-firefox-gnome-support ...
dpkg: error processing /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb (--unpack):
 trying to overwrite `/usr/lib/mozilla-firefox/components/libmozgnome.so', which is also in package firefox-gnome-support
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/mozilla-firefox_1.0.7-0ubuntu0.1_i386.deb
 /var/cache/apt/archives/mozilla-firefox-gnome-support_1.0.7-0ubuntu0.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

Mozilla firefox now refuses to work at all. I have had to install epiphany-browser to post here asking for help :(

Does anyone know how I can fix it?

Many thanks.

---

### Post by Xian on 2005-09-25
I use Opera Web Browser so I'm not absolutely sure here, but it would appear that you have four very similar pacakges installed. I would think you only need one set of these, and that the others are what is causing conflicts on your system.

- mozilla-firefox
- firefox
- mozilla-firefox-gnome-support
- firefox-gnome-support

---

### Post by mlomker on 2005-09-25
You are trying to install two different firefox packages, **firefox** and **mozilla-firefox**.

 I'm assuming one of them is from a non-ubuntu repository, such as backports.  Disable any of the 'extra' and 'backports' repositories and do an update.  That should allow the system to upgrade to the 1.07 that is in the *security* repository....that one works.

---

### Post by Milambar on 2005-09-26
That worked, mlomker, thank you.

---

### Post by ZephyrXero on 2005-10-06
This did not fix the problem for me. It looks like I had the backports one....so I just installed all things firefox and tried reinstalling them. It still won't work. Only thing is now Synaptic thinks it's installed fine, but when I try to start Firefox it never comes up.

---

### Post by mlomker on 2005-10-06
I'd remove the packages in Synaptic and then delete the package list files prior to reinstalling them. 

```

ls /var/lib/dpkg/info/*firefox* #see what is in there before you delete them
sudo rm /var/lib/dpkg/info/*firefox*

```

---

### Post by Kyral on 2005-10-06
[quote=mlomker]You are trying to install two different firefox packages, **firefox** and **mozilla-firefox**.

I'm assuming one of them is from a non-ubuntu repository, such as backports. Disable any of the 'extra' and 'backports' repositories and do an update. That should allow the system to upgrade to the 1.07 that is in the *security* repository....that one works.[/quote]

Actually Hoary-Backports is official now (use the one from Archive.Ubuntu.com)

---

