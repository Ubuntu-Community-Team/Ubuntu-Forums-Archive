---
title: "lucid upgrade trouble"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by jamoncillo on 2010-05-04
hi. I just upgraded to Lucid Lynx and had a couple of issues (the most annoying being the emerald window decorator, but that's fixed already)

However, I can't get gwibber to work, nor do I know how to make the minimize, maximize buttons appear on the left side, as they're supposed to be.

Thanks

---

### Post by jamoncillo on 2010-05-04
oh... also my Gnome-Do crashes all the time   >.< 
that's why it's better always performing a clean install, but I have so many programs installed I needed to keep =(

---

### Post by jamoncillo on 2010-05-04
ok, so I've tried several times and nothing. removed gwibber and reinstalled it (yeah, M$Win style) and still nothing, I get the   error when running it from terminal:

```
File "/usr/lib/python2.6/dist-packages/desktopcouch/local_files.py", line 189, in items_in_section
    raise ValueError("Section %r not present." % (section_name,))
ValueError: Section 'oauth_token_secrets' not present.
```


about the button layout, still nothing. It's still on the right side instead of the new, lefty =/
( I have done the gconf-editor thing, and it never changes no matter where I place the ' :  '    ). thought could be something about my window decorator ( I had to manualy reload emerald after upgrading), so I did 

```
gconftool-2 -s '/apps/metacity/general/compositing_manager' --type bool true
```


and nothing happened

---

### Post by jamoncillo on 2010-05-04
ok, so apparently the button layout stuff had something to do with the window decorator in use. I installed compiz fusion icon and noe if I switch from one to the other I get different button layouts. when using emerald, the 'regular' righty button layout; lefty when switching to GTK.

However, still no workaround for gwibbler \=

---

### Post by Lorne.Bouchard on 2010-05-04
> **jamoncillo said:**
> hi. I just upgraded to Lucid Lynx and had a couple of issues (the most annoying being the emerald window decorator, but that's fixed already)

However, I can't get gwibber to work, nor do I know how to make the minimize, maximize buttons appear on the left side, as they're supposed to be.

Thanks

I was unable to upgrade 9.10 nor install a fresh 10.4 on a Fujitsu Lifebook P7010. It seems that X is broken. Neither the installer nor the upgraded Ubuntu is able to open the display. The problem is probably due to a faulty Xconfig file. Native screen resolution is 1280×768. A previous Ubuntu 9.04 installation and a 9.10 upgrade worked fine...

Cheers!

---

### Post by jamoncillo on 2010-05-06
uhm.... did you manage to log into the live account? (obviously, using the CD/pen drive)

BTW, just for the record... I used the live cd and deleted everything but my personal files (pics, music, etc) including hidden files. INstalled a clean copy of lucid and now gibber works like a charm. however, I was tring to restore my installed programs with 
```

sudo dpkg --set-selections /home/package.selections && apt-get dselect-upgrade

```

but it just won't work. any ideas??

---

### Post by jamoncillo on 2010-05-07
ok. I'll tag this as solved, but the only workaround was clean install. Also I was having keyboard issues. My screen would freeze at startup, tought everything kept working (I could see my programs opening and loading, I just couldn't make any I/O)

my mouse pinter could move, tought coulnd't click anything, and my keyboard was also death. needed to log in and out several times, and I thing the solution was to unplug my laptop form the AC power to get it back to normal, regarding that screen issue

---

