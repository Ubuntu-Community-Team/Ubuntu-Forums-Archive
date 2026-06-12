---
title: "No kplayer icons/toolbars on upgrade to Karmic"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by ardzeii on 2009-12-25
Hello,

On my upgrade from Jaunty -> Karmic, the icons/toolbars in kplayer all went missing (except for the open file button). I wasn't sure what the problem is at first, and I even went as far as modifying my kplayerrc. I searched for kplayer packages, and the following were listed:

> kplayer - A KDE media player based on MPlayer
kplayer-data - Data files for kplayer
kplayer-doc - Documentation for kplayer

I installed **kplayer-data**, and the icons/toolbars are now all back. So... problem solved. However, I would just like to clarify the following:

1. Is kplayer-data a new package introduced in Karmic, but wasn't tagged as a dependency/suggested package of kplayer, and was therefore not installed in the upgrade? Or,
2. Does kplayer-data already exist in the previous repositories? Is there a "bug" in the latest kplayer package that makes it fail to list kplayer-data as a dependency/suggested package?

BTW, this is for Karmic 64 (I'm not sure if the same issue occurs in the other repositories).

Hope someone can clear this up. 

Thank you! :)

---

