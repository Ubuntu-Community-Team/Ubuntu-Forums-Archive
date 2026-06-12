---
title: "Missing UI Text in XMMS, Nero After Dist-Upgrade to Edgy"
date: 2007-01-25
forum: Installation &amp; Upgrades
---

### Post by LordMau on 2007-01-25
While checking for missing items after a dist-upgrade to edgy I noticed that the menus for xmms and the whole UI of nerlinux are missing text where there should be text. See my attached pics.

Any suggestion how to restore them?

Thanks!

---

### Post by LordMau on 2007-01-26
The NWN linux client installer also has no text. :( 

Some googling revealed a few entries at launchpad such as [here](https://launchpad.net/bugs/62300). The suggestion there however didnt work.

Anyone have a solution for this?

---

### Post by LordMau on 2007-01-26
Whaaa no replies still? :confused: 

Anyway solved it on my own (again lols).

With reference _[here,]("http://www.hydrus.org.uk/journal/etch-nv.html") _I made a .gtkrc file in your home directory that contained the following:
```
  style "user-font"
   {
    fontset="-monotype-arial-medium-r-normal-*-*-90-*-*-p-*-microsoft-cp1251"
   }

  widget_class "*" style "user-font"
```
I've read in other cases you may need to name the file .gtkrc.mine. In my case this did not work at all, so I used .gtkrc.

---

### Post by ravindran.k on 2007-04-15
Greetings!
I have the same problem ..this suggestion didnt work for me :( I have the issue in xmms, audacity, ardour..

any more ideas?

---

### Post by Siva Chandran P on 2007-12-10
Try changing your locale language settings to US

```
export LANG="en_US"
```

and launch XMMS from commandline and if it works change your language settings in System->Language Support

---

