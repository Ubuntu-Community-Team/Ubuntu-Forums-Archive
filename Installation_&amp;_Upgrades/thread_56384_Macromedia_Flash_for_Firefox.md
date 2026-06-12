---
title: "Macromedia Flash for Firefox?"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by rjpa on 2005-08-12
Hi,

I've read the unofficial Ubuntuguide on howto install Flashplayer for Firefox, but APT cannot find the package. And I've added backports to my sources.list properly.

How do I get Flashplayer installed???

Cheers

Update: I solved it, I used the wrong links for backports, the backports site says that we must use a mirror, but mirrors are not updated. Well, I changed back to preffered ones, and now it works, hurray.

---

### Post by shakin on 2005-08-12
All you should need to do is go to a page that uses Flash. There will be an icon in place of the Flash that you may need to click on. Firefox will automatically get Flash after asking you.

---

### Post by Gav-UK on 2005-08-13
it didnt work for me.

What i did was goto macromedia and download the linux flash player. then follow the instructions contained in the read-me file.

works fine after that

---

### Post by rjpa on 2005-08-13
[QUOTE=Gav-UK]it didnt work for me.

What i did was goto macromedia and download the linux flash player. then follow the instructions contained in the read-me file.

works fine after that[/QUOTE]

Well, I just set the "sources.list" to the one mentioned in "ubuntuguide" and then did a: apt-get update and then apt-get install firefox* So I get all the fonts and stuff correctly installed, it worked great that way.

---

