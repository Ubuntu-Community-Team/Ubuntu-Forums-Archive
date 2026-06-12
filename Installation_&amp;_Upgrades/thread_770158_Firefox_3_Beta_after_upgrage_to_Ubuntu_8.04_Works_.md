---
title: "Firefox 3 Beta after upgrage to Ubuntu 8.04: Works well only if launched using &quot;sudo&quot;"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by FireON on 2008-04-27
I've just upgraded to Ubuntu 8.04. Firefox 3 replaced my Firefox 2. But if I use standard launch button I can't add any bookmark, can't use search panel etc. If i use command line (**sudo firefox**) everything allright.

What I gotta do to launch "normal" Firefox using main menu (**firefox** without "**sudo**")?

---

### Post by ssam on 2008-04-27
sounds like you profile has got damaged.

First close all instances of firefox. then open you home folder and do View -> Show Hidden Files, the should be a .mozilla folder. inside that there is a firefox folder. right click on this and rename it to firefox.old

now start firefox. it should start with a clean profile. you will loose you bookmarks and saved passwords.

---

### Post by FireON on 2008-04-27
**ssam**, thanks a lot! That worked :KS

---

