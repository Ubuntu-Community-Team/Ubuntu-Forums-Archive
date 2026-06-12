---
title: "Problem with GIMP install serious!! :-("
date: 2010-03-31
forum: Installation &amp; Upgrades
---

### Post by maitraya on 2010-03-31
I uninstalled GIMP using sudo apt-get remove. Now I want to install it. So I typed sudo apt-get install gimp..... It gave me an error like this:

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  gimp: Depends: libgimp2.0 (>= 2.7.3) but 2.4.5-1ubuntu2 is to be installed
        Depends: libatk1.0-0 (>= 1.29.3) but 1.22.0-0ubuntu1 is to be installed
        Depends: libbabl-0.0-0 (>= 0.1.3-2010020903.1~ll) but it is not going to be installed
        Depends: libc6 (>= 2.11) but 2.7-10ubuntu3 is to be installed
        Depends: libdbus-glib-1-2 (>= 0.78) but 0.74-2 is to be installed
        Depends: libfontconfig1 (>= 2.8.0) but 2.5.0-2ubuntu3 is to be installed
        Depends: libgegl-0.0-0 (>= 0.1.2) but it is not going to be installed
        Depends: libglib2.0-0 (>= 2.22.0) but 2.16.6-0ubuntu1.2 is to be installed
        Depends: libgtk2.0-0 (>= 2.19.1) but 2.12.9-3ubuntu2 is to be installed
        Depends: libpango1.0-0 (>= 1.24.0) but 1.20.5-0ubuntu1.1 is to be installed
        Depends: libpoppler-glib4 (>= 0.12) but it is not installable
        Depends: librsvg2-2 (>= 2.26.0) but 2.22.2-2 is to be installed
        Depends: python-support (>= 0.90.0) but 0.7.5ubuntu1 is to be installed
E: Broken packages



PLEASE HELP ME FIX THIS PROBLEM!!!

---

### Post by LinuxTAd on 2010-03-31
Can you post your sources.list please? Something is not correct, it is trying to install an older version.

Also what Ubuntu release are you using?

You might want to also take a look at this post: [http://ubuntuforums.org/showthread.php?t=879926&page=2](http://ubuntuforums.org/showthread.php?t=879926&page=2)

---

### Post by maitraya on 2010-03-31
Thanks LinuxTAd, you were right. I had to remove two getdeb sources from the list and sudo apt-get install gimp worked perfectly.

Thanks for the good advice. ;):KS

---

