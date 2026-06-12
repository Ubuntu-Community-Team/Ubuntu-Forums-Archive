---
title: "Ubuntu updates &amp; Libreoffice."
date: 2016-12-21
forum: Installation &amp; Upgrades
---

### Post by Hewjr100 on 2016-12-21
I know ubuntu has security updates and others, including firefox.  But why don't they update libreoffice?  I just installed ubuntu 16.10, and I am not comfortable with ppa's.  Is it possible they might include libreoffice in updates, or will it ****be necessary to use ppa.

Henry[***[URL="https://www.google.com/search?client=ubuntu&hs=zNU&channel=fs&q=necessary&spell=1&sa=X&ved=0ahUKEwjN04icg4bRAhUBSSYKHUe0CRAQvwUIGSgA"][B]**]("https://www.google.com/search?client=ubuntu&hs=zNU&channel=fs&q=necessary&spell=1&sa=X&ved=0ahUKEwjN04icg4bRAhUBSSYKHUe0CRAQvwUIGSgA")*[/B][/URL]

---

### Post by The Cog on 2016-12-21
Once a version is released, it is not given updates other than bug fixes or security updates. This is for stability - they don't want new features borking people's otherwise working installations. So LibreOffice won't get updates (unless there is an important security uppdate, I guess). Even then, it would be a patch to the existing version, not a new LibreOffice version.

Personally, I tend to uninstall the LibreOffice that comes with Ubuntu and install the download straight from the LibreOffice website if I feel the need to update LO to the latest version.

---

### Post by ajgreeny on 2016-12-21
I have been using the ppa for LO for a long time now with no difficulties for me or my system.
[https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa?field.series_filter=xenial)

I am now using LO Version: 5.2.3.2 - Build ID: 1:5.2.3~rc2-0ubuntu1~xenial1 which runs very well.  The packages for this ppa are built by LibreOffice itself I believe so there is no real problem of badly built packages in this ppa.

---

### Post by Hewjr100 on 2016-12-21
Does the LO website have a deb file?

Henry

---

### Post by The Cog on 2016-12-21
> **Hewjr100 said:**
> Does the LO website have a deb file?

Henry

Yup.
[http://www.libreoffice.org/download/libreoffice-fresh/](http://www.libreoffice.org/download/libreoffice-fresh/)
Download the main program, the help and your language user interface (GB for me).
Drop the three files in the same directory. Right click the three files and "extract here" for each of them. Open a command prompt in the same directory as the tar.gz files and run this command:
```
sudo dpkg -i Libre*/DEBS/*.deb
```
I always uninstall the default installed libreoffice packages first.

---

### Post by vasa1 on 2016-12-21
Just to add to what The Cog wrote, if you do install direct from the LibO site, make sure you choose the .deb! I've found myself mistakenly downloading the .rpm!

But, of late, I've been using the ppa that ajgreeny mentioned.

---

### Post by Hewjr100 on 2016-12-21
Looks easy as long as it does not add a ppa.  Will give it a shot tomorrow.

Henry

---

### Post by vasa1 on 2016-12-21
> **Hewjr100 said:**
> Looks easy as long as it does not add a ppa.  Will give it a shot tomorrow.

Henry
Installing directly from [www.libreoffice.org/download](www.libreoffice.org/download) doesn't add a ppa.

---

### Post by ajgreeny on 2016-12-22
> **Hewjr100 said:**
> Looks easy as long as it does not add a ppa.  Will give it a shot tomorrow.

Henry
Why are you so anxious about using a PPA?

I agree there are risks related to using PPAs, which anyone can create, but for a group of packages such as LO, I feel very happy to use the PPA, and it can, of course, be removed just as easily as it's enabled by using ppa-purge.

I am not sure if there are statistics of the number of users, but I suspect that there must be very many for that LO PPA, and I am fairly sure any dangerous bugs or problems would quickly become public knowledge and the bugs squashed.

---

### Post by Hewjr100 on 2016-12-22
I had problems in the past,. besides, it makes it easier to upgrade to the next version.  Upgraded fro 16.04 to 16.10, yes I disabled ppas, but it did not really matter, I dad to remove them anyway, and install newer ppas for current version. Having said that I prefer not to use ppas.

Henry

---

### Post by Hewjr100 on 2016-12-22
Last night I uninstalled LO and install the deb packages.  what do you know, today LO 5.2.4 was released!  I got lucky, I did not remove LO, all I did was download new version, and extract deb files to downloads folder.  Then I ran sudo dpkg -i *.deb and it installed over 5.2.3 with no problems.  Thanks for all your help and replies.

Henry

---

### Post by Hewjr100 on 2016-12-22
Well Today I downloaded and install LO 5.2.4.  Easy peasy.

Henry

---

