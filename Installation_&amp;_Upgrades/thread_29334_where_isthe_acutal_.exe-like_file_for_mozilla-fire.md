---
title: "where isthe acutal .exe-like file for mozilla-firefox/"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by Dex on 2005-04-23
I know I can launch mozilla-firefox from places/internet/mozilla-firefox browser. But  - where is the actual 'click here' file where it would accomplish the same, like .exe file in windoze that acutally launches the browser?

---

### Post by Seth on 2005-04-23
[QUOTE=Dex]I know I can launch mozilla-firefox from places/internet/mozilla-firefox browser. But  - where is the actual 'click here' file where it would accomplish the same, like .exe file in windoze that acutally launches the browser?[/QUOTE]
 /usr/lib/mozilla-firefox/

---

### Post by Nis on 2005-04-23
/usr/bin/firefox

No exe extension in Linux.

---

### Post by Seth on 2005-04-23
[QUOTE=Nis]/usr/bin/firefox

No exe extension in Linux.[/QUOTE]
 OP: note that this is a symlink only.

---

### Post by crazybill on 2005-04-24
**/usr/lib/mozilla-firefox**  is the working directory.

Type

#**cd /usr/lib/mozilla-firefox** 

and then at

/usr/lib/mozilla-firefox # **ls -F**

You will see the binary files with * after them  including **firefox***

---

