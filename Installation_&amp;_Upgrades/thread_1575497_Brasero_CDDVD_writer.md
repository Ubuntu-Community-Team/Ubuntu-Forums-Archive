---
title: "Brasero CD/DVD writer"
date: 2010-09-15
forum: Installation &amp; Upgrades
---

### Post by gpdas on 2010-09-15
I installed Ubuntu 10.04 in my Dell Laptop. I found Brasero is working fine. I installed it in my IBM Thinkcenter desktop. But Brasero is giving error '[SIZE=3][COLOR=Red]libdvdcss[/COLOR][/SIZE][SIZE=3][COLOR=Red].so.2[/COLOR][/SIZE]' is not available!!!  How?

---

### Post by flick on 2010-09-15
That is a library for reading encrypted DVDs. Most DVDs are. To get that library :

DVD Playback

Most commercial DVDs are encrypted with Content Scrambling System (CSS), which attempts to restrict the software that can play a DVD. You'll need to install libdvdcss if you want to play them. You can do so by first installing the libdvdread4 package via Synaptic Package Manager or Terminal.

Click here to install libdvdread4

Then, within a Terminal window, enter:

sudo /usr/share/doc/libdvdread4/install-css.sh

Source : [http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html](http://blog.thesilentnumber.me/2010/04/ubuntu-1004-post-install-guide-what-to.html)

---

### Post by gpdas on 2010-09-17
libdvdread4 is already installed. But still its not working.

---

### Post by lonewaster on 2011-01-15
[CENTER]**_ISSUE RESOLVED_**
[/CENTER]

To fix this issue, all I had to do was-

[CENTER][LEFT]
[LIST=1]
[*]**Open A Terminal Window**
[*]**_REMOVE_ *libdvdread4* by running the following in the Terminal Window:**```
***sudo apt-get remove libdvdread4***
```
[*]_**RE-INSTALL**_** *libdvdread4* again by running the following in the Terminal Window: **```
***sudo apt-get install libdvdread4***
```
[/LIST]

That was it. I am even copying a DVD now!! :popcorn:
[/LEFT]
[/CENTER]

---

### Post by lonewaster on 2011-01-15
[U][B]*removed*
sorry for the multipost- kept getting proxy error from site.
  [/B][/U]

---

### Post by lonewaster on 2011-01-15
[U][B]*removed*
sorry for the multipost- kept getting proxy error from site.
  [/B][/U]

---

### Post by lonewaster on 2011-01-15
[CENTER]**_ISSUE RESOLVED_**
[/CENTER]
 
To fix this issue, all I had to do was-

[CENTER][LEFT]
[LIST=1]
[*]**Open A Terminal Window**
[*]**_REMOVE_ *libdvdread4* by running the following in the Terminal Window:**```
***sudo apt-get remove libdvdread4***
```
[*]_**RE-INSTALL**_** *libdvdread4* again by running the following in the Terminal Window: **```
***sudo apt-get install libdvdread4***
```
[/LIST]

That was it. I am even copying a DVD now!! :popcorn:
[/LEFT]
[/CENTER]

---

### Post by lonewaster on 2011-01-15
[CENTER]**_ISSUE RESOLVED_**
[/CENTER]
 
To fix this issue, all I had to do was-

[CENTER][LEFT]
[LIST=1]
[*]**Open A Terminal Window**
[*]**_REMOVE_ *libdvdread4* by running the following in the Terminal Window:**```
***sudo apt-get remove libdvdread4***
```
[*]_**RE-INSTALL**_** *libdvdread4* again by running the following in the Terminal Window: **```
***sudo apt-get install libdvdread4***
```
[/LIST]

That was it. I am even copying a DVD now!! :popcorn:
[/LEFT]
[/CENTER]

---

### Post by lonewaster on 2011-01-15
[CENTER]**_ISSUE RESOLVED_**
[/CENTER]
 
To fix this issue, all I had to do was-

[CENTER][LEFT]
[LIST=1]
[*]**Open A Terminal Window**
[*]**_REMOVE_ *libdvdread4* by running the following in the Terminal Window:**```
***sudo apt-get remove libdvdread4***
```
[*]_**RE-INSTALL**_** *libdvdread4* again by running the following in the Terminal Window: **```
***sudo apt-get install libdvdread4***
```
[/LIST]

That was it. I am even copying a DVD now!! :popcorn:
[/LEFT]
[/CENTER]

---

### Post by lonewaster on 2011-01-15
[CENTER]**_ISSUE RESOLVED_**
[/CENTER]
 
To fix this issue, all I had to do was-

[CENTER][LEFT]
[LIST=1]
[*]**Open A Terminal Window**
[*]**_REMOVE_ *libdvdread4* by running the following in the Terminal Window:**```
***sudo apt-get remove libdvdread4***
```
[*]_**RE-INSTALL**_** *libdvdread4* again by running the following in the Terminal Window: **```
***sudo apt-get install libdvdread4***
```
[/LIST]

That was it. I am even copying a DVD now!! :popcorn:
[/LEFT]
[/CENTER]

---

