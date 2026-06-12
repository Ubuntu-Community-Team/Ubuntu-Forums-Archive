---
title: "Firefox update notification"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by Oldhacker on 2010-01-06
I am using Firefox 3.5.6 at present. Yesterday and today, I got a very brief flash announcement in the lower right hand corner of my screen that Firefox update 3.5.7 was now available. However, it disappeared so fast that I could not read all of it and learn where and how I should go to accomplish the update.

---

### Post by slakkie on 2010-01-06
It is not available in Lucid, so I doubt it is available in other versions..

---

### Post by sliketymo on 2010-01-06
> **Oldhacker said:**
> I am using Firefox 3.5.6 at present. Yesterday and today, I got a very brief flash announcement in the lower right hand corner of my screen that Firefox update 3.5.7 was now available. However, it disappeared so fast that I could not read all of it and learn where and how I should go to accomplish the update.

You may want to consider adding the mozilla-daily ppa to your apt-sources list if you would like to have the latest versions.

http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu<version>main

http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu<version>main(Source Code)

---

### Post by kansasnoob on 2010-01-06
> **Oldhacker said:**
> I am using Firefox 3.5.6 at present. Yesterday and today, I got a very brief flash announcement in the lower right hand corner of my screen that Firefox update 3.5.7 was now available. However, it disappeared so fast that I could not read all of it and learn where and how I should go to accomplish the update.

You probably have the native Mozilla Firefox installed, perhaps via Ubuntuzilla.

Just close Firefox and in the Terminal run:

```
gksudo firefox &
```

Firefox will open as root (you won't see personalized settings, bookmarks, etc - that's OK), so just click on Help > Check for Updates and let it do it's thing. 

When asked to restart Firefox do so. You still won't see personalized settings but just close Firefox, close the terminal, and then open Firefox as normal.

Click on Help > About Mozilla Firefox and you should see you have 3.5.7.

---

### Post by kansasnoob on 2010-01-06
BTW if you're running i386 (32 bit) there's a new Ubuntuzilla repo that makes updates work just like all Ubuntu updates:

[http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Installation)

There is no urgent need to update to that method though. If you have more questions go here:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

---

### Post by Oldhacker on 2010-01-06
You probably have the native Mozilla Firefox installed, perhaps via Ubuntuzilla.

Just close Firefox and in the Terminal run:

Code:

gksudo firefox &

Firefox will open as root (you won't see personalized settings, bookmarks, etc - that's OK), so just click on Help > Check for Updates and let it do it's thing.

When asked to restart Firefox do so. You still won't see personalized settings but just close Firefox, close the terminal, and then open Firefox as normal.

Click on Help > About Mozilla Firefox and you should see you have 3.5.7.

Following this procedure, I got a strange result: It opened Firefox 3.5.7 with the usual welcome screen. However, when I restarted Firefox, I am back to 3.5.6!!! 

There is nothing urgent about updating to 3.5.7, but I would like to know what is happening.

Thanks for the input

---

### Post by nanotube on 2010-01-06
Hi
hmm, well, it seems that your 'normal' way of starting firefox may be pointing at /usr/bin/firefox-3.5 (which is the ubuntu-repos version), rather than /usr/bin/firefox (which is the ubuntuzilla version, if you have it installed).

so, first, post your output of 
```
ls -al /usr/bin/*firefox*
``` just to see if you even have ubuntuzilla version

and second, look at the properties of your menu shortcut (or whatever you use to 'start firefox normally' (as in, without gksudo), and see where it points.

---

### Post by Oldhacker on 2010-01-07
This morning, when I booted up and opened Firefox, the new 3.5.7
was there, complete with congratulations!

All is well that ends well, but thanks for the inputs.

---

### Post by nanotube on 2010-01-07
> **Oldhacker said:**
> This morning, when I booted up and opened Firefox, the new 3.5.7
was there, complete with congratulations!

All is well that ends well, but thanks for the inputs.

heh nice. i love a problem that solves itself! :)

---

