---
title: "[SOLVED] After reinstalling Ubuntu, how to preserve up/down torrents on ktorrent?"
date: 2008-09-25
forum: Installation &amp; Upgrades
---

### Post by ezphilosophy on 2008-09-25
I am planning to change my dual-boot partitions/hard drive setup and have to reinstall Windows and Ubuntu.

However, I want ktorrent to "remember" all of my torrents being uploaded and downloaded so that when I reinstall, I just have to install ktorrent and everything will be the same as before.

It seems that all the info is being stored in /home/[myname]/.kde/share/apps/ktorrent/

I wonder if I just copy my whole home folder and put it back as was, will it work?  Are all the settings/info in there?

---

### Post by pytheas22 on 2008-09-25
> I wonder if I just copy my whole home folder and put it back as was, will it work? Are all the settings/info in there?

Yes, that *should* work, as long as both the torrented files and the torrent data itself are in that directory.

In fact, since you're reinstalling Ubuntu, you may want to consider [creating a separate partition for /home]("http://www.psychocats.net/ubuntu/separatehome").  This makes it really easy to preserve all of your personal settings even if you reinstall Ubuntu completely.

---

### Post by ezphilosophy on 2008-09-25
Yeah, I've thought about doing that back when aysiu wrote it up.  Never got around to it.

Well, I'm still looking for confirmation from someone but knowing me, I will just go ahead and do the reinstall and face the consequences later.  :)

---

### Post by ezphilosophy on 2008-09-26
Well, it worked!

Just to be clear:
I reinstalled ubuntu and then installed ktorrent.  I copied over all my torrents (all in a folder called "torrents" where ktorrent was previously configured to download/upload to/from) and then, I copied over the .kde directory in the home folder and replaced anything it asked me for.

I loaded up ktorrent and it started with all my uploads/downloads as it was before.  

Hope this can help someone else.

---

### Post by ezphilosophy on 2008-09-26
Well, it worked!

Just to be clear:
I reinstalled ubuntu and then installed ktorrent.  I copied over all my torrents to the same location as before (all in a folder called "torrents" where ktorrent was previously configured to download/upload to/from) and then, I copied over the .kde directory into the home folder and replaced anything it asked me for.

I loaded up ktorrent and it started with all my uploads/downloads as it was before.  

Hope this can help someone else.

---

