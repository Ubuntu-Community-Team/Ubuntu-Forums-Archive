---
title: "Trouble with upgrade to 10.04 LTS on Dell Vostro V13"
date: 2011-03-24
forum: Installation &amp; Upgrades
---

### Post by mtnmama on 2011-03-24
Hi, 

New to forums. Pretty new to ubuntu.  I am currently running Ubuntu9.04 (Jaunty) on a Dell Vostro v13, pre-installed when I got it. I would like to upgrade to the 10.04 LTS but when I try, all goes fairly well until I get to the screen where it wants to set up my keyboard (Step 3). Then comp freezes and I have no use of touch-pad or keyboard, have to just shut off computer and re-install to factory settings to use it again. I have upgraded with USB and through update manager. Neither works. No clean instal from a CD because I don't have a CD drive... I have read in a couple places the inability to use keyboard/touch pad might have to do with the incorrect driver on the VostroV13... does anyone have similar problem or know how I can fix this? 

Thanks

---

### Post by zvacet on 2011-03-25
You can not skip versions,so first you have to upgrade from 9.04 to 9.10 and then to 10.4.Read [this]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty") to get details.

---

### Post by Old_Grey_Wolf on 2011-03-25
> **zvacet said:**
> You can not skip versions,so first you have to upgrade from 9.04 to 9.10 and then to 10.4.Read [this]("https://help.ubuntu.com/community/EOLUpgrades/Jaunty") to get details.

I though I should clarify this a little for anyone finding this post by using a search engine.

It is true that you can not upgrade from 9.04 to 10.04; however, it is not true that you can not skip versions. You can upgrade from a Long-Term-Support (LTS) version to another LTS version. LTS versions are labeled [**even **numbered year].[04]. You can upgrade from 8.04 to 10.04 and 10.04 to 12.04 without going through the intermediate versions.

The reason you can not upgrade from 9.04 to 10.04 is that 9.04 is not an LTS version...9.04 = [**odd **numbered year].[04].

---

