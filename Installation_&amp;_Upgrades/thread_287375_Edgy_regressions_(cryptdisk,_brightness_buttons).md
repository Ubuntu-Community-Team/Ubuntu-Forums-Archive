---
title: "Edgy regressions (cryptdisk, brightness buttons)"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by alspnost on 2006-10-28
Hi guys - I replaced my Dapper install today with a clean install of Edgy, and I'm mostly loving it.  For one thing, it's noticeably faster all round - even OpenOffice feels snappier than ever!

But there are a few of killer regressions.  Firstly, the LiveCD wouldn't boot at all (CPU#0 soft lockup error), until I enabled my wireless with the (un)kill switch.  Strange, but at least it's a workaround.

Second - I have an encrypted /home partition, standard LUKS setup, and the cryptdisk stuff just doesn't happen on boot.  So I can't login, with no homedir, other than via a failsafe login, manually fixing the mount etc.  This really sucks - I know crypt disks are not a default Ubuntu setup, but it's still a very bad regression from Dapper, where everything worked perfectly every time.  What's the best way of hacking the init scripts to fix this?

Finally - the Fn+screen brightness keys on my laptop have stopped working.  Or to put it more strongly, they used to change my screen brightness (ahem), now they just slaughter the X server and drop me back to the console.  That's really, really bad news.  Now why would something like this change so dramatically for the worse?  The other laptop functions keys still work (volume etc), but the screen brightness keys are a really nasty regression.  Can I remap them in some way (it's Fn + up/down cursor keys)?  I can live with it not working, but *not* killing my entire session when I hit them on reflex.

If I can fix these issues, then Edgy will rock my universe like nothing else!

Cheers
AL

---

