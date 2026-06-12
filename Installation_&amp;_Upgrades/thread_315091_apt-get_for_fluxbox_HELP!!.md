---
title: "apt-get for fluxbox HELP!!"
date: 2006-12-08
forum: Installation &amp; Upgrades
---

### Post by 200mg on 2006-12-08
i've done

#apt-get update
#apt-get upgrade
#apt-get install fluxbox (as root)
and it can't find package

matter of fact it seems like all the how to's i read mention an apt-get method of installing alot of packages but it only workds like 1/3 the time for me

I've also tried this....

root@trace:/# apt-cache search fluxbox
root@trace:/#

when i do apt-cache search it just returns to prompt, doesn't say anything

root@trace:/# dpkg -S fluxbox
dpkg: *fluxbox* not found

when i try the dpkg method i get file not found

---

### Post by lhtown on 2006-12-08
Fluxbox is in the "universe" repository. You have to enable that. You can use synaptic or directly edit /etc/apt/sources.list

```
sudo gedit /etc/apt/sources.list
```

---

