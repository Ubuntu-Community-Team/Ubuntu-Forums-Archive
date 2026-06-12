---
title: "Broken package problem"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by comastalker on 2006-11-06
I don't really know where to put this and am quite sad, that only 10 days after trying ubuntu (I normally use gentoo) I'm at the point of complete helplessness I used to feel with windows. Well I'll get to the point:

I followed the article in the ubuntu-wiki regarding the lexmark printer driver (Z615). I followed the instructions which told me to download bin-
tarballs from lexmark, decompress, convert from rpm to deb and install them.

Well alien -i on the lexmark rpm fails silently, so I tried using alien -d and dpkg -i which throws error messages telling me there is no /etc/init.d/cups.

Oups. Don't think that's it ;) 

Well I'm not that stupid, I just thought I already installed cups(d). "It's not too late" I thought and started Synaptic -> Oups Error Message (there's a broken package z600cups that has to be removed). 

Synaptic doesn't load any package lists, so cups installation has to wait. 

I did a dpkg -r z600cups which tells me it's a bit f***ed up and has to be reinstalled first. And that's exactly where we dive into circularism: 

- I can't install because there's no cups 
- I can't install cups, because Synaptic wants z600cups to be removed 
- dpkg -r doesn't like removing things, that aren't predictable.

What shall I do now? In gentoo I would have manually repaired everything, but ubuntu is great in hiding mechanisms...

Don't feel offended by the distro blabla - but this has been the reason, why I used gentoo and after a long decade of regaining the power to believe into simplicity there followed a short decade of frustration. Frustration I had to express ](*,) 

Thanks to anyone willing to help me,
Paul Hilbert

---

### Post by Joe_CoT on 2006-11-06
```
sudo apt-get install -f
```

That will attempt to fix any broken package dependencies.

---

### Post by comastalker on 2006-11-07
That didn't help - it reports the same as dpkg -r PACKAGE.

```

ln -s /etc/init.d/cupsys /etc/init.d/cups

```

made it.
I didn't know /etc/init.d/cupsys is the same as /etc/init.d/cups.
Here is a similiar solution for a brother printer:
[http://www.kubuntu.de/forum/forum.php?req=thread&id=5258]("http://www.kubuntu.de/forum/forum.php?req=thread&id=5258")

Thanks anyway Joe.

---

