---
title: "Can't get flash work in Natty 64 Bit"
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by Abilnet on 2011-05-13
During the past days, I've tried "everything" to get flash working in my fresh Natty 64 Bits install to my Acer Aspire 5745G -laptop. I've read countless of hours through the forums, but none of the tips have helped in my case. Using the latest Firefox and Chromium.

For example, I've downloaded the 64 Bits "libflashplayer.so" from Adobe:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)

...and put it into:
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins

...and restarted the browsers, even the entire PC, but still flash doesn't work.

What an I doing wrong? ...help very much appreciated!

---

### Post by oldos2er on 2011-05-13
Have you tried FlashAid? [https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

---

### Post by Abilnet on 2011-05-13
Thanks for the tip, I'd try FlashAid but unfortunately not success (even the test script jammed and never finished)

**HOWEVER, CASE SOLVED!**

I did the following, helped at least in my case:

1.) Uninstalled Flash Plugin Installer from Ubuntu Software Center. Also, make sure you don't have flash option selected in "Restricted Extras" (Ubuntu Software Center)
2.) Downloaded Flash for 64 Bits (flashplayer10_2_p3_64bit_linux_111710.tar.gz) from:
[http://labs.adobe.com/downloads/flashplayer10_square.html](http://labs.adobe.com/downloads/flashplayer10_square.html)
3.) Extracted file: "libflashplayer.so" from the file above
4.) Deleted older versions/traces to "libflashplayer.so" from directory:
```
/usr/lib64/mozilla/plugins
```
5.) Copied the "libflashplayer.so" to the plugins directory:
```
sudo cp libflashplayer.so /usr/lib64/mozilla/plugins
```
6.) Restarted my PC
7.) Flash is working!

Hope this helps others, too

---

### Post by electricgolem on 2011-08-01
Thanks, Abilnet - this worked well and I have Flash back on my machine.:D

---

### Post by mikey on 2011-08-11
hp pavilion dev9607us
1 gig ram
nvidia 7150m graphic card

installed natty with wubi and had the same flash issue. installed flash aid in ff and bingo flash is NOW working perfectly. thanks for the help.:)

---

