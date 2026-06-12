---
title: "Java &amp; Firefox"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2005-10-30
I installed Java in /usr/local/j2re.4.2_09. It seems I have to manually install the plugin for it to work with Firefox. I have to make a symbolic link in Firefoxs's Plugin directory.
Using the above location for Java, what would I type for a symbolic link? Apparently it goes like "ln -s /usr/local/"   then what??

---

### Post by paddyg on 2005-10-30
[QUOTE=AllanP]I installed Java in /usr/local/j2re.4.2_09. It seems I have to manually install the plugin for it to work with Firefox. I have to make a symbolic link in Firefoxs's Plugin directory.
Using the above location for Java, what would I type for a symbolic link? Apparently it goes like "ln -s /usr/local/"   then what??[/QUOTE]

ln  -s   /usr/local/j2re.4.2_09/jre/plugin/i386/ns7/libjavaplugin_oji.so   /usr/lib/mozilla-firefox/plugins

(or wherever your firefox plugin folder is)

---

