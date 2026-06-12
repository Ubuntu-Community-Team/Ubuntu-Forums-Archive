---
title: "Ubuntu Mate 15.04 flash player firefox google chrome chromium"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by alekkova on 2015-04-18
Ubuntu Mate 15.04: flashplayer for firefox, google_chrome and chromium is posible to make to work!

---

### Post by alekkova on 2015-04-18
For all who need libflashplayer.so to work with firefox and other browser, I found how to make it work.

---

### Post by alekkova on 2015-04-18
Short explain is:
Delete libpepflashplayer.so
Make a link from libflashplayer.so to libpepflashplayer.so
And it works.

---

### Post by hachikosan on 2015-05-07
Alekkova,

can you share the actual terminal command that you use..... please

---

### Post by mattharris4 on 2015-05-08
Is it possible to just install Pepper Flash as we have been in 14.04?  Here are instructions:  [http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04](http://www.omgubuntu.co.uk/2014/06/install-pepper-flash-chromium-ubuntu-14-04) (this now works with either Chromium or Firefox).

---

### Post by alekkova on 2015-06-10
I put new lines in /etc/rc.local and every time you reboot your computer you have readjusted Flash player:
mcedit /etc/rc.local
Insert two lines:
rm /usr/lib/mozilla/plugins/libfreshwrapper-pepperflash.so
ln -s /usr/lib/mozilla/plugins/libflashplayer.so /usr/lib/mozilla/plugins/libfreshwrapper-pepperflash.so
And F2 to save your work.

I apologize for the slow response, I was absent, fieldwork.

---

