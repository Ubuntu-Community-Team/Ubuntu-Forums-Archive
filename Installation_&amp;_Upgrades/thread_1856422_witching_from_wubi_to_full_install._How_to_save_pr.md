---
title: "witching from wubi to full install. How to save programs?"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by vikash_chandola on 2011-10-08
I am running Ubuntu 11.04 (installed with wubi) since a month. Now i am going to make it's proper dual boot with windows 7(using bootable USB stick). Is there any way to save all those programs that i have already downloaded and installed(vlc,GIMP,VM etc) through Ubuntu software center. I know they are in my computer(in cache folder) but how to reuse them on other installation.I don't want to download those softwares once again that's why i am asking you. 
thanks for reply it will really helps me a lot.

---

### Post by sanderd17 on 2011-10-08
Well, if you're going to upgrade to 11.10 in a few days, you will need to download them again (since they will have new versions).

So I really wouldn't bother about it and wait a few days before you go to a real installation.

---

### Post by vikash_chandola on 2011-10-08
> **sanderd17 said:**
> Well, if you're going to upgrade to 11.10 in a few days, you will need to download them again (since they will have new versions).

So I really wouldn't bother about it and wait a few days before you go to a real installation.
Yes i will install 11.10 but tell me how can i save all those softwares that are installed in my computer right now. Is it possible tosave them??

---

### Post by sanderd17 on 2011-10-08
All wubi things are stored in the file C:\ubuntu\disks\root.disk

You can mount that file from inside Ubuntu and use all the files. They are just .deb files, so you can install them by double clicking.

But with the first update (in a few days), they will have to be downloaded anyway.

---

### Post by pkg9991 on 2011-10-08
if it's not wubi and we installed it as a separate installation of ubuntu is there a way to backup all downloaded softwares and have not to download them again on new installation of Ubuntu

---

### Post by vikash_chandola on 2011-10-08
> **pkg9991 said:**
> if it's not wubi and we installed it as a separate installation of ubuntu is there a way to backup all downloaded softwares and have not to download them again on new installation of Ubuntu
[size=+2]How to do it???[/size]

---

### Post by sanderd17 on 2011-10-08
take a look at apt-on-cd

---

### Post by raja.genupula on 2011-10-08
> **pkg9991 said:**
> if it's not wubi and we installed it as a separate installation of ubuntu is there a way to backup all downloaded softwares and have not to download them again on new installation of Ubuntu


Hi man , if the installation is going for same version then i agree with you . But this software is not going to applicable for new versions because we gonna face dependencies problems.
But some application not going to face dependencies problems even though you have new distribution.but most of the applications going face dependencies issue for new distributions.

so no use if keep them.

---

### Post by vikash_chandola on 2011-10-08
> take a look at apt-on-cd great i made iso using this tool. How to install it on other installation. 
IS there any special way or this
```

sudo dpkg --install <package_name>

```there is a tutorial [here]("https://help.ubuntu.com/community/APTonCD") but i think those screenshots are on old ubuntu versions. I did not found any such thing like ** tools->[B]Repository** in my ubuntu,
[/B]

---

### Post by sanderd17 on 2011-10-08
it's now under software-center -> edit -> software sources

---

### Post by vikash_chandola on 2011-10-08
Is there any way to install these package's ISO without burning it in CD.
I have made proper dual boot of Ubuntu now want to install those packages.

---

### Post by raja.genupula on 2011-10-08
well i think you can extract the pkg's from ISO.then you can go with what you wanna do.

---

### Post by blazemore on 2011-10-10
I wrote a blog post on this a while back.
[http://www.blazemore.net/2011/09/how-to-move-your-wubi-installation-to.html](http://www.blazemore.net/2011/09/how-to-move-your-wubi-installation-to.html)

---

### Post by vikash_chandola on 2011-10-10
> **blazemore said:**
> I wrote a blog post on this a while back.
[http://www.blazemore.net/2011/09/how-to-move-your-wubi-installation-to.html](http://www.blazemore.net/2011/09/how-to-move-your-wubi-installation-to.html)
very good blog.

---

### Post by Hylas de Niall on 2011-10-26
> **sanderd17 said:**
> They are just .deb files, so you can install them by double clicking.

Is that all i must do after using AptOnCD to transfer back my downloaded .deb's?

I've been looking, and the only bit of the process that doesn't seem to be properly explained to the layman is how to actually reinstall the programs! LOL!

---

