---
title: "Tex-common don't work after upgrade to 10.04"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by tompa78 on 2010-09-13
Hi! I've just upgraded from ubuntu 8.04 LTS to 10.04 LTS.

During the installation I received the error message that tex-common could not be installed. After searching the forum and bugs, I found these 

[https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/580881](https://bugs.launchpad.net/ubuntu/+source/tex-common/+bug/580881)
[https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/228334](https://bugs.launchpad.net/ubuntu/+source/texlive-base/+bug/228334)

talking about dependencies issues, with the solution to first install texlive-base. I have now tried to remove all tex packages completely and reinstall them, starting with texlive-base, but I keep getting the same error. 

"Running updmap-sys. This may take some time... 
updmap-sys failed. Output has been stored in
/tmp/updmap.mRqqSyLA
Please include this file if you report a bug."

Looking in that file it says 

"updmap: Scanning for Map entries:
updmap: using map file `/usr/share/texmf-texlive/fonts/map/dvips/amsfonts/euler.map'
updmap: using map file `/usr/share/texmf/fonts/map/dvips/lm/lm-cs.map'


!!! ERROR! The map file `mt-plus.map' has not been found at all.

    Either put this file into the right place or remove the
    reference from the configuration files - see
    update-updmap(1)."

What do I do now? Please help! I'm rather new at this, and certainly no expert on Linux... 

Can I find this map file somewhere and put it in its right place manually, or is there some other swift and magic Linux command that you experts know of that could try?

Thanks!

---

### Post by tompa78 on 2010-09-13
Ok, so now I've discovered that my title is a bit wrong. tex-common actually does install fine. But I still can't get LaTex to work. The problem is that updmap failes because it can't find the map 'mt-plus.map' when I try to install say texlive-base. 

Even if I disable that map, with "updmap -disable mt-plus.map", it just complain about missing the next map, 'mt_yy.map'. 

Does anyone have any clue on what I could do to get those maps? I'm at a loss here!

Thankful for _any_ suggestions!

---

### Post by tompa78 on 2010-09-14
Alas, no reply from anyone...

Anyway, I can of course fix the problem by disabling the maps "mt-plus.map" and "mt-yy.map". Then I can build the whole texlive library successfully. 

I still leave this as an open question though, because I actually don't even know what those font maps do or if they have been replaced by anything else. If anyone know, please tell me. 

Also, if anyone know how I could install texlive with those two font maps, I would be grateful!

Thanks!

---

