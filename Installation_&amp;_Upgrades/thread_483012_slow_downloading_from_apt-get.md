---
title: "slow downloading from apt-get"
date: 2007-06-24
forum: Installation &amp; Upgrades
---

### Post by huangja on 2007-06-24
When I download from apt-get, I can't get over 10 kb/s while downloading. Most of the time, its downloading at about less than 5 kb/s. 

To be fair, I am in China right now, but it downloaded much quicker a couple days ago, so I dont think thats the problem. Also, axel and bittorrent both download at reasonably fast speeds as well. 

I tried deleting the "us." from the sources.list files, but that didnt work.

Anyone know of another cause that might make this slow? Thanks

---

### Post by davidjmayo on 2007-06-24
where is apt-get looking for the files

is it looking at the archive in china or somewhere else eg US or UK?

---

### Post by huangja on 2007-06-25
I'm not sure. There used to be the us extension on the url's in sources.list, but i already removed them, and its still slow. 

Are there archives in China? If so, how would i go about accessing them?

---

### Post by davidjmayo on 2007-06-25
from my limited experience (1 week) I found this

I installed using alternate cd as live cd wasn't doing anything. I don't know if there would be a difference between the installs

 i think in the install the order was select keyboard layout  (follow the key tests) then country (maybe the other way round)

so anyway i selected the country i'm in - currently vietnam

when i went to a repos (archive) it showed as http;/vn.archive etc etc

not only was it very slow down to b/s not kb/s (bittorent and other internet apps were running at normal speeds) but many files were not found or timed out for example 
lib**** or python files
Anything ending in en (english) was also hard to get/find

i didn't look in and sources.list as i didn't know about it. So obviously it was never edited too.

anyway i ended up doing a reinstall and this time chose country as UK (i guess US would work too but i'm from UK)

This fixed my problem and downloads come at my max speed and no errors finding files or timing out

I don't know if the country can be changed without a reinstall as i didn't look into that but i would think it's possible somehow

hope this helps

---

