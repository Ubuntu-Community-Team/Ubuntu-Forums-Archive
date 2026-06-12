---
title: "What's installed in 11.10"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by dreamquartz on 2012-01-01
I asked the other day what's running, and that worked indeed.

I also would like to know what's installed. How can I find out what is installed?

The reason for this question is that I seem to have a problem with Adobe Acrobat Reader.
I was able to install directly from Adobe a while back, but since 2 days the pull down menus did not show any text anymore.

I thought simple thoughts, and tried to re-install.
I used the version available @ Ubuntu Software, under the name Acroread, thinking the faulty version will be replaced, and I will remain a happy camper.

Arrggggh ](*,).

It turns out to be that under "Dash home" there are now 2, yes 2, icons showing "Acrobat Reader 9" as installed. One icon is working, but the other is not.

Removed Acroread, tried to remove the .bin install version from Adobe, which did not work anymore.
Tried to re-install the .bin version from Abode. That does not work either.
So re-installed Acroread, because I need Acrobat, but now the 2 icons are present.

I can not find where the icons are located, but more importantly, I do not know if there are any residual files left, and how to get rid of them.

Can anyone please guide me in the right direction.

Thx,

Dream

---

### Post by darkod on 2012-01-01
To remove completely, you use:
sudo apt-get --purge remove <package>

For the version in Software Center the package name is acroread. Not sure about the one you installed with .bin. Also, if you needed to extract the downloaded file, look in the folder where you extracted as there might be an uninstall script.

---

### Post by dreamquartz on 2012-01-02
Thanks:D

---

