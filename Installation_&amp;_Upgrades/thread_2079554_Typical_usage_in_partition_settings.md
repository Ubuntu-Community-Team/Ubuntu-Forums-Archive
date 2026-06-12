---
title: "Typical usage in partition settings"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by celsiusat on 2012-11-02
[COLOR=#222222][FONT=Arial]Hi all [/FONT][/COLOR]

[COLOR=#222222][FONT=Arial] whenever I install ubuntu linux using alternate install cd , i will encounter this screen [/FONT][/COLOR]

[http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=partition-settings.png](http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=partition-settings.png)


[COLOR=#222222][FONT=Arial]now when I press typical usage I will get the following screen [/FONT][/COLOR]

[http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=DSCN0684.jpg](http://s529.photobucket.com/albums/dd339/aarklon/?action=view&current=DSCN0684.jpg)



[COLOR=#222222][FONT=Arial]Does anyone know why or when you might choose another option besides "typical"?? (options such as news, largefile, largefile4 etc) [/FONT][/COLOR]

                                              **   [COLOR=#222222][FONT=Arial]OR[/FONT][/COLOR]**
[COLOR=#222222][FONT=Arial] the pratical example situations where options such as news, largefile, largefile4 etc are used ? [/FONT][/COLOR]

---

### Post by jerome1232 on 2012-11-02
All they do is fine tune the inode ratio, news being the most inodes and largefile4 being the fewest.

news is for lots and lots and lots of small files, while largefile4 is for fewer very large files.

---

