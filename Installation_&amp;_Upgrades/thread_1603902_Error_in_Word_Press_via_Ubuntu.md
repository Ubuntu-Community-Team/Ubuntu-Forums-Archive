---
title: "Error in Word Press via Ubuntu"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by Safinaz Yusof on 2010-10-23
Hey there, 

Appreciate if any of you could assist me in handling the below issue :-

I'm having difficulties in installing/upgrading my WordPress version and theme.  The error note as below ..

_A . Installing/Upgrading_
Update WordPress
Downloading update from [http://wordpress.org/wordpress-3.0.1.zip…](http://wordpress.org/wordpress-3.0.1.zip…)

Unpacking the update…

**Could not create directory.: /public_html**

**Installation Failed**


_B. Installing Theme_

Installing Theme: WP-Creativix 1.5.5
Downloading install package from [http://wordpress.org/extend/themes/download/wp-creativix.1.5.5.zip…](http://wordpress.org/extend/themes/download/wp-creativix.1.5.5.zip…)

Unpacking the package…

**Could not create directory. /public_html**

Pls help.Thanks !

---

### Post by mörgæs on 2010-10-24
Hi, welcome to the forum. 

It sounds like you do not have enough rights for creating /public_html (I assume that you are creating this in /var). Does it work if you use **sudo**?

---

