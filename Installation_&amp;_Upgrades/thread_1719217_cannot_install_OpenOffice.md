---
title: "cannot install OpenOffice"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by HappyLinux on 2011-04-01
I've currently got running on my system OO3.2.1 provided by the default repository. However, I want to install OO3.3.

The only way I can find is by downloading it from the website and installing from there. However, I've found a problem. I don't know how.

The download comes in a .tar.gz file. I know that is the Linux version of a compressed archive or something.

I extract the contents into its own folder and the result is a mass of files that are confusing the heck out of me.

There's a couple of readme files and license files, but there are 49 .deb files.

How do I install OO from this mess? Where do I begin?

---

### Post by uRock on 2011-04-01
cd the terminal to the directory that you have the debs in and run the folling command to install them all at once. ```
sudo dpkg -i *.deb
```
If you haven't already done so, you need to first remove the default install of OpenOffice, then install the new version.

---

### Post by Hagar Delest on 2011-04-01
See [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by HappyLinux on 2011-04-02
Everything worked great. I had to go through Synaptics instead of Software Manager to remove the old OOo as some remains were left being which prevented the new one from installing.

Cheers.

---

