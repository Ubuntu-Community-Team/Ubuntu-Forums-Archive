---
title: "Synaptic. At home: direct connect. At work: proxy"
date: 2008-11-11
forum: Installation &amp; Upgrades
---

### Post by ciro314 on 2008-11-11
I would like to automatically configure synaptic to connect to a proxy at work and direct connect at home. Any idea? 

i.e. To run firefox I have made a little script like this:

if iwconfig | grep -i 'ESSID:"home_essid"'
then
	firefox
else
	firefox -P profile_at_work(connect through proxy)
fi

---

