---
title: "How to install the java plugin on firefox 3.6"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by ownsuall on 2010-01-24
[COLOR="Red"]I've recently installed firefox 3.6 but java dosent work =(. I have firefox installed in my /home/owner/downloads directory. My flash plugin still works so how do i get the java plugin to work?
[/COLOR]

nvm i solved it using [http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29](http://sourceforge.net/apps/mediawiki/ubuntuzilla/index.php?title=Main_Page#Java_plugin_not_showing_up_.28on_Ubuntu_Karmic.29)

---

### Post by eMJayy on 2010-01-25
Thanks! That was exactly what I needed!

---

### Post by gorg_karlo on 2010-02-04
Got into the same exact situation after installing Firefox (Namoroka) 3.6

64-bit users - take note:

After making sure that sun-java6-plugin is installed, cut and paste the following command:

> sudo update-alternatives --install /usr/lib/mozilla/plugins/libjavaplugin.so mozilla-javaplugin.so /usr/lib/jvm/java-6-sun/jre/lib/amd64/libnpjp2.so 50

---

### Post by binukavumkal on 2010-10-03
THANK YOU VERY MUCH :guitar:

After trying different solutions, this exactly worked!.

The issue I identified in my case is

The firefox is installed as a part of Clean installation Hardy Heron.

I upgraded this to 9.04.

I noticed that this Firefox installation does not have any plug in directory and i had to create it manually in ~/.mozilla directory.

I have already installed the JRE 1.6 Update 20.

Thanks once again

---

