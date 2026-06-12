---
title: "How to get OpenOffice.org 2.0.3 in Dapper Drake?"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by Aleksandersen on 2006-11-14
Hi,

How can I upgrade the default OpenOffice.org 2.0.2 installation that comes with Ubuntu Dapper Drake to version 2.0.3 or newer?

I need to upgrade as I bought the [Sun Weblog Publisher extension](http://store.digitalriver.com/servlet/ControllerServlet?Action=DisplayPage&Env=BASE&Locale=en_GB&SiteID=sunstor&id=ProductDetailsPage&productID=50984800) for OpenOffice.org without realising it required a newer version of OOo than Ubuntu provided.

Can anyone help me out here?

---

### Post by Paul41 on 2006-11-14
You can download 2.0.4 from the OpenOffice site ([http://www.openoffice.org/)](http://www.openoffice.org/)). You can only get it as an RPM package from there, but you can convert it with alien.

To get alien:
```
sudo aptitude install alien
```

After you download the files from the OpenOffice site, unpackage the files. Then change to the directory where the .rpm files are. Then type
```
sudo alien -d *.rpm
```
Using *.rpm will convert all of the files at once so you don't have to do it one at a time.

Then to install
```
sudo dpkg -i *.deb
```

Here is a guide on alien in case this isn't clear :-D [https://help.ubuntu.com/community/RPM/AlienHowto](https://help.ubuntu.com/community/RPM/AlienHowto)

---

### Post by Scunizi on 2006-11-21
Alien will work.  The most current version is 2.2.13.  Is this what is in Edgy?  You can also download it directly from Oo as a tar.  I haven't tried to install it this way beccause it involves uninstaling the current version.  I don't know if it will break anything on install.

---

### Post by petersjm on 2006-11-30
I'm just converting the downloaded .rmp files to .deb with Alien. Do I *really* have to uninstall the Ubuntu version (2.0.2) before installing the debs? I guess I'll need to back up all my files first...

---

### Post by Aleksandersen on 2006-11-30
Why convert?

When there are ready .deb files available for download...

[http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/2.0.4-RC3/OOo_OOD680_m5_LinuxIntel_install_nn_deb.tar.gz](http://ftp.linux.cz/pub/localization/OpenOffice.org/devel/680/2.0.4-RC3/OOo_OOD680_m5_LinuxIntel_install_nn_deb.tar.gz)
(found via openoffice.org)

---

### Post by Paul41 on 2006-11-30
> I'm just converting the downloaded .rmp files to .deb with Alien. Do I *really* have to uninstall the Ubuntu version (2.0.2) before installing the debs? I guess I'll need to back up all my files first...

Yes, you should uninstall version 2.0.2 first. Your Writer, Calc, etc. files will be OK because they are stored on the file system and not in OpenOffice itself.

> Why convert?

When there are ready .deb files available for download...

[http://ftp.linux.cz/pub/localization..._nn_deb.tar.gz](http://ftp.linux.cz/pub/localization..._nn_deb.tar.gz)
(found via openoffice.org)

A .deb would remove the step of converting. When I looked i didn't find a .deb on the OO site.

---

### Post by petersjm on 2006-11-30
@Paul41: Thanks. I figured as much. All rpms converted now and I'll install the debs after I uninstall 2.0.2. Thanks for your reply :)

@Aleksandersen: Hmmm. I didn't know there were any 2.0.4 debs available. Maybe I should have looked harder! Thanks anyway.

---

### Post by petersjm on 2006-12-01
Just an update. I managed to install all the converted debs for 2.0.4 and everything went swimmingly. It seems this version doesn't have the quickstart utility (at least, not that I can find), but it definitely seems to start up faster than the distro-version. I had gotten used to clicking the tray icon to create a new document, but I'll get over it LOL.

---

### Post by ArchVile on 2006-12-04
do you really think one should uninstall the openoffice.org package before upgrading? the ubuntu-desktop package depends on it !!! -- i would strongly advise against that procedure...

also, does one lose any integration when upgrading? i had by-hand installations of ooo under earlier versions of ubuntu (when there was no xubuntu and i was doing server-installs of ubuntu plus manual install of all other packages using xubuntu for desktop), and integration sucked big time then...

so, does anyone know of a safe way of getting ooo 2.0.4 under dapper? any unofficial repo that has ubuntu-specific debs?

thanks,
archie

---

### Post by Paul41 on 2006-12-04
>  do you really think one should uninstall the openoffice.org package before upgrading? the ubuntu-desktop package depends on it !!! -- i would strongly advise against that procedure...

All you are doing is removing the ubuntu-desktop version of OpenOffice. The ubuntu-desktop package just gives you everything that comes by default, so removing OpenOffice won't hurt anything.

---

### Post by larvar on 2006-12-14
How do I uninstall ubuntu version?

---

### Post by Paul41 on 2006-12-14
> How do I uninstall ubuntu version?

```
sudo apt-get remove openoffice.org
```

---

