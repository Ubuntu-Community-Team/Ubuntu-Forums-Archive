---
title: "Firefox 5 on Hardy Heron 8.04 on a Toshiba Satellite"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by davesmith on 2011-08-07
For those who are obliged to run obsolete LTS distros because their Toshiba Satellite is old, but they want to run the latest version of the excellent Firefox browser, here is a solution.

1) Download the latest Linux tarball  - Firefox-5.0.1.tar.bz2 - from

[http://www.mozilla.com/products/download.html?product=firefox-5.0.1&os=linux&lang=en-US](http://www.mozilla.com/products/download.html?product=firefox-5.0.1&os=linux&lang=en-US)

2) Extract the archive to a convenient directory using Archive Manager

3) Since you installed the new version by hand, there won't be an icon in  Applications -> Internet.  Therefore, the default Firefox is still  using the older version. Remove the older version of Firefox first  using synaptic, or:-

 Code <Sudo apt-get remove Firefox>

4) To create an icon  for the new version, place a cursor on the top panel and click the right  button -> Add to Panel... -> Custom Application Launcher ->  Add.

For Name:, type Firefox.

For Command:, type in the complete path to where you have unpacked it or use the Browse... option to browse to the unpacked Firefox shell script icon

You can add whatever you want in the Comment field if you wish.

5) If you wish to have an icon for the new version of firefox in  Applications -> Internet, then click System -> Preferences ->  Main Menu -> Internet -> Firefox Web Browser -> Properties.  In  the Command: field, type in the complete path to the new version of Firefox or use the Browse... option to navigate to where you've unpacked it and point it to the Firefox shell script icon.                                                                                               

6) In Firefox - Edit - Preferences - Advanced - Update, be sure to tick the automatic updates box

Sorted!

---

