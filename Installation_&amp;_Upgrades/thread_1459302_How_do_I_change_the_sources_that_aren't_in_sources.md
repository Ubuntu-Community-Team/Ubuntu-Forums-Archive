---
title: "How do I change the sources that aren't in sources.list?"
date: 2010-04-21
forum: Installation &amp; Upgrades
---

### Post by Phyxiis on 2010-04-21
My title pretty much explains it.

I am running Jolicloud on my netbook (which I believe is an Ubuntu derivative) and I am tried to enter the getdeb.net sources in so I can install apps from the website through APT but 

1) When I entered the sources into sources.list and then the key into Terminal and then went to the site and tried to install an app it didn't work.

2) I deleted the line of code in the sources.list file and when I opened terminal and entered "sudo apt-get update" it showed the list of sources, but on the list were Getdeb.net sources. 

My question is how do I delete sources that aren't in /etc/apt/sources.list ?

---

### Post by drs305 on 2010-04-21
Some repositories are entered into the /etc/apt/sources.list.d folder. Check to see if the repository is listed in that folder. 

They may also be listed in Synaptic's "Other Software" tab (System, Administration, Synaptic. Settings, Repositories, Other Software tab).

---

### Post by sisco311 on 2010-04-21
System -> Administration -> Software Sources -> Other Software tab or check out the /etc/apt/sources.list.d/ directory ;).

EDIT: d'oh! drs305 has beaten me to it! :)

---

### Post by Phyxiis on 2010-04-21
Thank you very much. This is why I love Linux over Windows XD

The problem was that in "/sources.list.d/getdeb.list" was that apparently with Jolicloud it puts "robbin" instead of "jaunty" which it is based off of. 

Thanks again

---

### Post by Phyxiis on 2010-04-21
This is off topic but the Quick Reply isn't working for me

---

### Post by Phyxiis on 2010-04-21
Nevermind. This topic is solved, for me at least

---

### Post by sisco311 on 2010-04-21
You can mark this thread as solved.

At the top of the page, click the "[COLOR="Red"]Thread Tools[/COLOR]" Menu and then "Mark this thread as Solved".


> **Phyxiis said:**
> This is off topic but the Quick Reply isn't working for me

You have to click the [IMG]http://ubuntuforums.org/images/buttons/quickreply.gif[/IMG] button to activate the Quick Reply. It's at the bottom right, next to the Quote & Multi-Quote buttons.

---

