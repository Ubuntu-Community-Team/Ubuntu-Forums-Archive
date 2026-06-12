---
title: "error in wine"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by davidtuti on 2008-03-03
Hi

I have Ubuntu 7.10 and when I try to run wine it says me an error:

err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
fixme:msvcrt:__lconv_init  stub
fixme:heap:HeapSetInformation 0x110000 0 0x458b00 4
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
err:ole:CoGetClassObject class {304ce942-6e39-40d8-943a-b913c40c9cd4} not registered
err:ole:CoGetClassObject no class object {304ce942-6e39-40d8-943a-b913c40c9cd4} could be created for context 0x1
fixme:heap:HeapSetInformation 0x610000 0 0x458b00 4

I saw these:

root@david-desktop:/usr/bin# set | grep -i display
root@david-desktop:/usr/bin# echo $DISPLAY

root@david-desktop:/usr/bin# 


Any help? Thanks a lot and sorry for my english

---

### Post by zvacet on 2008-03-03
After installing Wine did you run in terminal **winecfg**?If you didn´t do it now.

---

