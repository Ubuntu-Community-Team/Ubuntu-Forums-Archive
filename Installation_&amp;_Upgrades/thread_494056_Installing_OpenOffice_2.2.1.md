---
title: "Installing OpenOffice 2.2.1"
date: 2007-07-06
forum: Installation &amp; Upgrades
---

### Post by xlinuks on 2007-07-06
Hi,
How can one install/upgrade to OpenOffice 2.2.1. I currently have FF and thus OpenOffice 2.2.0.
I found on [www.openoffice.org](www.openoffice.org) only the RPM packages.
The only 2 ways are to dive into the developer section and compile the source code or to wait for Gutsy Gibbon?
I'm willing it that much cause I heard there have been fixed a lot of issues, perhaps printing too.

---

### Post by kspringer on 2007-07-06
Or use Alien to translate the RPMs into DEBs.
It should be in the Repos.

---

### Post by xlinuks on 2007-07-06
Thanks!
 I used Alien to translate to .deb and then install every package one by one.
I wish they would consider .deb users too. I was impressed when I went to the skype site and it took me right to the Linux install page where the first option was Feisty Fawn. That was great.

---

### Post by DawgPoP on 2007-08-13
hey, i'm a newb and ubuntu  feisty is my first linux OS.  I used alien to convert each of the rpms to debs.  then i installed debs.  Now, how do I start it, add shortcuts on my applications and make it my default application in Gnome?

---

### Post by stchman on 2007-08-14
> **xlinuks said:**
> Thanks!
 I used Alien to translate to .deb and then install every package one by one.
I wish they would consider .deb users too. I was impressed when I went to the skype site and it took me right to the Linux install page where the first option was Feisty Fawn. That was great.

After you converted all the .rpm files to .deb files you could have opened up a terminal and typed:

sudo dpkg -i *.deb

and installed all the .deb files.

Don't forget to install the desktop integration .deb file as well.

---

### Post by ka1ssr on 2007-08-24
I converted the RPM files to deb files, ran sudo dpkg -i *.deb and now I can't get OpenOffice to run.  The menu items for the application have dissappeared and when I type "openoffice" at a command line prompt I get a message telling me that openoffice isn't installed.  Did I goof somewhere?

Thanks for your help.

Bill

---

