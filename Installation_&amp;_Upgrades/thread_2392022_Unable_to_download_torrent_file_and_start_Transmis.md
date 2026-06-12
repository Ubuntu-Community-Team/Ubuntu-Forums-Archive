---
title: "Unable to download torrent file and start Transmission"
date: 2018-05-15
forum: Installation &amp; Upgrades
---

### Post by Dada_Maheshvaranan on 2018-05-15
I just installed 18.04 Bionic Beaver on my new Lenovo Ideapad 320. Suddenly, when I locate a Torrent file I want and click to download, it no longer opens Transmission. The first time I did it, it started to play the movie (a popular one with many seeders). Now nothing happens. And, of course, it does not appear in my Downloads file, because that only happens after Transmission starts to leech it.

---

### Post by uRock on 2018-05-16
Does it work when you attempt a legal download, such as an ubuntu ISO?

---

### Post by SeijiSensei on 2018-05-17
It's likely the order of file handlers changed.  Right-click a torrent link in your browser and choose the option to save it to your system.  Then open a file browser and right-click on the file.  The default handler appears at the top of the list.  My guess is that it is not Transmission, though you should be able to select it from the list that is presented.  I don't know how to change the order of handlers in vanilla Ubuntu (I use Kubuntu), but you should be able to find out from a quick Google search.

Operating systems and programs don't handle files differently depending on whether a torrent points to a legal file or not.

---

### Post by uRock on 2018-05-17
> **SeijiSensei said:**
> Operating systems and programs don't handle files differently depending on whether a torrent points to a legal file or not.My concern is that it was a bad magnet file.  Testing a trusted torrent link would help in troubleshooting.

---

