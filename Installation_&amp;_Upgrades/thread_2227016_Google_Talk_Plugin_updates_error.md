---
title: "Google Talk Plugin updates error"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by M.Yusuf_YILMAZ on 2014-05-30
Hi

I'm trying to install Google talk plugin but does not worked on Ubuntu 12.04. I tried several times remove and re-install but still same error. I'm new user about Ubuntu When i use sudo apt-get update it says 


W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_talkplugin_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems



How can i fix it ?

---

### Post by bapoumba on 2014-05-30
You have a duplicate entry in your sources.list. Please post the output to :
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d
```

It most probably is in one of your ppa (you can also check from Software Sources).

---

### Post by M.Yusuf_YILMAZ on 2014-05-31
Ok. Those are output

for the [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list[/FONT][/COLOR]
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise main universe restricted multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise-backports universe main multiverse restricted

for the [COLOR=#000000][FONT=Ubuntu Mono]ls /etc/apt/sources.list.d
[/FONT][/COLOR][COLOR=#000000][/COLOR]
danielrichter2007-grub-customizer-precise.list
danielrichter2007-grub-customizer-precise.list.save
ehoover-compholio-precise.list
ehoover-compholio-precise.list.save
google.list
google.list.save
google-talkplugin.list
google-talkplugin.list.save
groovy-dev-grails-precise.list
groovy-dev-grails-precise.list.save
tualatrix-ppa-precise.list
tualatrix-ppa-precise.list.save
ubuntu-x-swat-x-updates-precise.list
webupd8team-y-ppa-manager-precise.list
webupd8team-y-ppa-manager-precise.list.save

---

### Post by bapoumba on 2014-05-31
Please post the output to :
```
cat /etc/apt/sources.list.d/google.list
cat /etc/apt/sources.list.d/google-talkplugin.list
```
There most probably are duplicate entries for the same repository here.

---

### Post by M.Yusuf_YILMAZ on 2014-05-31
for the [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list.d/google.list[/FONT][/COLOR]
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

for the [COLOR=#000000][FONT=Ubuntu Mono]cat /etc/apt/sources.list.d/google-talkplugin.list[/FONT][/COLOR][COLOR=#000000]

[/COLOR]
[COLOR=#000000][/COLOR]
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main
deb [http://dl.google.com/linux/talkplugin/deb/](http://dl.google.com/linux/talkplugin/deb/) stable main

---

### Post by bapoumba on 2014-05-31
As the entry in /etc/apt/sources.list.d/google-talkplugin.list is the same as /etc/apt/sources.list.d/google.list (and even duplicated), you can remove that file.
If you prefer, you can move it to your /home and delete it later once everything is fine :
```
sudo mv /etc/apt/sources.list.d/google-talkplugin.list ~
```

Now **sudo apt-get update** should work.

---

### Post by M.Yusuf_YILMAZ on 2014-06-03
Thank you very much for your help. It worked for me.  Thanks again. :)

---

### Post by bapoumba on 2014-06-03
You are most welcome :)
Please mark your thread as solved (under Thread tools), thanks.

---

