---
title: "need gui for Karmic Koala"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by Lakeside5 on 2010-06-08
Ok, I've installed Karmimc Koala server edition, and I  wanted the gui so I followed advice on a forum and did an apt get install gnome desktop etc.  but don't know what to do next, all I see is a command line, no gui.  I would even settle for just having web min so I could control my server from that, as I have read that servers are more vulnerable with a gui.....and my last ubuntu server got hacked, so I had to wipe out the hard drive and start all over. I would appreciate any help, thanks.

---

### Post by zvacet on 2010-06-09
If you installed ubuntu-desktop metapackage then

```
startx
``` 

or

```
/etc/init.d/gdm start
```

---

### Post by garvinrick4 on 2010-06-09
If more assistance needed"

```
aptitude show gdm
```


Make sure installed.

---

### Post by Lakeside5 on 2010-06-10
Great! Thanks guys I shall try.  Zvacet I love your signature and 
garvinrick4 I love your avatar :)

---

