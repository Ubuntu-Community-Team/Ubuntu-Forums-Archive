---
title: "Upgrade from 6.1 to 7.1"
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by VShagios on 2008-03-31
Yesterday I installed 6.06 on a PIII 500Mhz PC because 7.1 would not mount the CD-ROM using the CD image.  I have now updated everything to 6.1 and want to go to 7.1, hoping that this will allow 7.1 to mount the CD-ROM using what ever driver the 6.1 is using.  
My problem is that when  using Applications->System->Update Manager, like the upgrade instructions say to do, I get the message that my system is up to date.  Am I missing something, or is there an other way to upgrade to 7.1?

---

### Post by zvacet on 2008-03-31
You can not upgrade from Edgy to Gutsy directly.It goes like this Edgy>Feisty>Gutsy.Go to the system>admin>software properties>check all under ubuntu software and updates tab.Reload.System>admin>update manager>you should see message **new version available**.If this doesn't work check your sources list.

```
gksudo gedit /etc/apt/sources.list
```

If you find two sources list,one with Dapper ans second with Edgy delete Dapper one.After that repeat above.

---

### Post by Pumalite on 2008-03-31
Wait till April 24th and you'll be able to go straight from 6.06 to 8.04
[http://ubuntuforums.org/showthread.php?t=695700](http://ubuntuforums.org/showthread.php?t=695700)

---

