---
title: "unable to download ttf-mscorefonts-installer 16.04"
date: 2016-12-06
forum: Installation &amp; Upgrades
---

### Post by 7-webmaster on 2016-12-06
Since the last security update I keep getting a prompt reporting that it was unable to download ttf-mscorefonts-installer.  Clicking on retry just results in a repetition of the error. I tried to do a search on this forum for issues but the search tool will not accept "ttf-mscorefonts-installer" as a search key.

---

### Post by PaulW2U on 2016-12-06
See this thread - [ttf-mscorefonts-installer broken?]("https://ubuntuforums.org/showthread.php?t=2343669") - for a work around that will enable you to install the MS fonts.

---

### Post by bcschmerker on 2016-12-06
In Software and Updates, confirm that Multiverse packages are selected.  The Package ttf-mscorefonts-installer (Miscellaneous - Graphical) is classified as Multiverse/X11.  It is possible that ttf-mscorefonts-installer has been discontinued, in which case ttf-root-installer (Fonts), which is classified as Multiverse/Fonts, will substitute.

---

### Post by howefield on 2016-12-07
If the above fails, you could install the 3.6 version of the package.

```
wget http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb -P ~/Downloads
```

will download the package to your Downloads folder, and
 
```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by 7-webmaster on 2016-12-07
> **PaulW2U said:**
> See this thread - [ttf-mscorefonts-installer broken?]("https://ubuntuforums.org/showthread.php?t=2343669") - for a work around that will enable you to install the MS fonts.

Thanks.  I really just want the nagware to go away since the only reason I have the truetype fonts is to read mail sent from M$ Outlook.

---

### Post by 7-webmaster on 2016-12-09
> **7-webmaster said:**
> Thanks.  I really just want the nagware to go away since the only reason I have the truetype fonts is to read mail sent from M$ Outlook.

I have tried removing the files indicated in the main thread but I continue to get the nagware.

---

### Post by vasa1 on 2016-12-09
> **7-webmaster said:**
> ... I tried to do a search on this forum for issues but the search tool will not accept "ttf-mscorefonts-installer" as a search key.
Try
```
ttf-mscorefonts-installer site:ubuntuforums.org
```in Google

---

### Post by howefield on 2016-12-09
Try..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

---

### Post by 7-webmaster on 2016-12-10
I don't want to download the fonts.  The only reason I have them is to read e-mail sent from M$.  I just want to stop the nagware.

---

