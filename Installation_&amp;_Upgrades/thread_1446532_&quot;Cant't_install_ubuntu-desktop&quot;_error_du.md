---
title: "&quot;Cant't install ubuntu-desktop&quot; error during upgrade from 804LTS-&gt;810"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Paulzy on 2010-04-04
Read [this post first]("http://ubuntuforums.org/showthread.php?t=1446508"), as this may be the cause of this issue. 

But as this is a different matter I would like a solution this new problem regarding upgrading from 840LTS to 810.

When attempting to upgrade to 9.10 I followed the correct upgrade path: 804LTS->810->904->910

I did as the instructions said, and setup the Software Sources to include Normal updates. It began as normal, but then stopped with this error:

"Can't install ubuntu-desktop"

Is my previous kubuntu-desktop install causing this error? Should I follow then the Kubuntu directions? I'm really confused here.

[upgradeError.png]("http://gallery.pjcii.net/displayimage.php?album=58&pos=27")
[http://gallery.pjcii.net/albums/userpics/10001/upgradeError.png](http://gallery.pjcii.net/albums/userpics/10001/upgradeError.png)

---

### Post by zvacet on 2010-04-05
On login session select **gdm** and then try to upgrade.You can also remove Kubuntu with 

```
sudo tasksel remove kubuntu-desktop
```

I will not do upgrade a way you try to do it.To much downloads and possible errors.If I´m you I will wait for one more month and make direct upgrade from Hardy to Lucid. ;)

---

