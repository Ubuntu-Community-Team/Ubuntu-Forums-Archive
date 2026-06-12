---
title: "Lucid - search for installed PPAs"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by trumpeteersman on 2010-12-19
I had some major bugs with KDE 4.3 and 4.4 and the only way that I could fix them was to install the entire KDE 4.5. This was mid-Summer.  Now I would like to upgrade to Maverick the proper way and have 4.5 in a stock repo.

I managed to get most of kde back to stock by luck and uninstall/reinstalling kdebase stuff and kubuntu-desktop a couple of times. A pain in the neck trying to find important packages that are already installed from a previous PPA. 
BTW my sources.list is stock right now.

Does anyone know of a way to search for installed PPA packages that are not in the stock repository?

---

### Post by karthick87 on 2010-12-19
Look in the origin section of the synaptic,

[IMG]http://imgur.com/l1QRR.png[/IMG]

---

### Post by trumpeteersman on 2010-12-19
karthick87's advice only works for individual packages. I wanted to search ALL packages.

I wrote a small inefficient bash script to work for me. It gets all installed packages and outputs the name followed by the version:

```

#!/bin/bash

SEARCHKEY=\~ppa
MYPAK=`dpkg --get-selections | awk '{ print $1 }'`

for i in $MYPAK
do
dpkg -l $i | grep -i $SEARCHKEY | head -6 | tail -1 | awk '{ print $2 "        " $3}'

done
                                                             

```

---

