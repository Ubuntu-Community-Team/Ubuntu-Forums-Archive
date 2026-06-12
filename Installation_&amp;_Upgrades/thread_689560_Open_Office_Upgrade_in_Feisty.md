---
title: "Open Office Upgrade in Feisty"
date: 2008-02-06
forum: Installation &amp; Upgrades
---

### Post by measekite on 2008-02-06
I am currently using Open Office 2.20 under Feisty.  I want to keep Feisty.  When using Base the Form and Query Wizards do not work after you create a new DB and table.  I heard this is corrected in the latest stable version.

(There is not excuse for this basic bug)

I would appreciate a detailed HowTo to be able to install the upgrade which I believe can be downloaded in rpm format.

I do not think that Ubuntu is properly maintaining the upgrades for these types of products especially since Gutsy came out for the older releases which should still be maintained for 18 months.

I hope that Canonical will in the future maintain newer releases of the applications that were shipped with a specific version.  It is a real pain to have to upgrade an entire OS just to get a new version of an application.

Repeating my request

**I would appreciate a detailed HowTo to be able to install the upgrade which I believe can be downloaded in rpm format.**

---

### Post by forestpixie on 2008-02-06
there is a deb download now which makes it a bit easier - [http://download.openoffice.org/2.3.1/index.html](http://download.openoffice.org/2.3.1/index.html)

then, assuming it's downloaded to desktop

```
cd Desktop

tar zxvf OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz

cd OOG680_m9_native_packed-1_en-US.9238

mv openoffice.org-kde-integration_2.3.1-9_i386.deb

sudo dpkg -i *.deb
```

that should all work - got the most from phorolinux's [page]("http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html") , but changed bit's where the version has changed - hope that's some help

this worked for me few days ago - at least I think I've got it right :)

---

### Post by measekite on 2008-02-07
> **forestpixie said:**
> there is a deb download now which makes it a bit easier - [http://download.openoffice.org/2.3.1/index.html](http://download.openoffice.org/2.3.1/index.html)

then, assuming it's downloaded to desktop

```
cd Desktop

tar zxvf OOo_2.3.1_LinuxIntel_install_en-US_deb.tar.gz

cd OOG680_m9_native_packed-1_en-US.9238

mv openoffice.org-kde-integration_2.3.1-9_i386.deb

sudo dpkg -i *.deb
```that should all work - got the most from phorolinux's [page]("http://phorolinux.com/how-to-installing-openofficeorg-23-on-ubuntu-linux.html") , but changed bit's where the version has changed - hope that's some help

this worked for me few days ago - at least I think I've got it right :)

Thanks

I did a similar version to the above and it worked.  The -1 *.deb is what really did it.  I never installed anything that had a bunch of debs at once.

One difficult thing that I had to do that was time consuming was installing by hand all of the executables in the menu and on the launch bar.

One thing is left and so far I cannot figure it out.

[B]I cannot find the icons for writer, calc, base, draw, impress etc that will show on the launch bar in in the menus.  They must be buried somewhere in one of the installation libs.  If anyone had found them please let me know.

I found the icons but was not able to install them in the usual way.  I did find another deb file called in the folder desktop integration and ran that.  It installed the appropriate executables in the "application>office menu system with the icons.  I then added them to the launch panel.

This is the only step that needed to be added to the code above.  I did not execute the line that begins with mv since I was not sure what it did or if it was really needed.

Thanks again.

PS.  This exercise is what is wrong with Linux and why it is not as popular as it should be on the desktop.  Red Hat, Suse, Mandriva, Ubuntu and others need to develop a standard for installs like what Windows has.  It is great to have Gnome, Kde and others as GUI but a standard install adopted by all distributions is badly needed.  Once this happens then Linux can be poised to take market share away from Windows.
[/B]

---

### Post by Hagar Delest on 2008-02-07
Are you sure there is not a missing step? Don't you have a desktop-integration folder for the menus and icons??? See here: [[Ubuntu] Installing OOo on Debian and Co.](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by forestpixie on 2008-02-07
Yep - a missing step there was - there was that in mine he remembers - but I wasn't going to download it again to find the name of the folder it was in - hence the link to phorolinux so the op could check it out - obviously he/she didn't :)

---

### Post by Hagar Delest on 2008-02-07
Anyway, even the linked page is outdated: OOo is delivered in .debs now and the integration step is also missing in the process.

---

