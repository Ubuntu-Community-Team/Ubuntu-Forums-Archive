---
title: "AptGet/Offline/PrintUris (upgrade) (ubuntu18.04)"
date: 2020-02-20
forum: Installation &amp; Upgrades
---

### Post by sacarde on 2020-02-20
hi,
   I follow this guide:  [https://help.ubuntu.com/community/AptGet/Offline/PrintUris](https://help.ubuntu.com/community/AptGet/Offline/PrintUris)

all works using command "apt-get --print-uris --yes install...mypackage", but dont works for command:

sudo apt-get --print-uris upgrade 

I dont view urls


is possible to generate urls for "upgrade" command?


thank you

---

### Post by sacarde on 2020-02-20
I redirect my question in "askubuntu"

[https://askubuntu.com/questions/1211937/aptget-offline-printuris-upgrade-ubuntu18-04](https://askubuntu.com/questions/1211937/aptget-offline-printuris-upgrade-ubuntu18-04)

---

### Post by deadflowr on 2020-02-20
It wouldn't post anything if there were no updates available.

---

### Post by sacarde on 2020-02-21
[https://paste.ubuntu.com/p/SZRtTMJ3Y5/](https://paste.ubuntu.com/p/SZRtTMJ3Y5/)

---

### Post by deadflowr on 2020-02-21
> Need to get 0 B/547 MB of archives.

You already have everything downloaded.
So it's not fetching any more information for you.
It doesn't need to.

What you can test/try is to clean out the cached downloads with apt clean.
(Or if you want you can keep the archives but move them to a temporary location
```
sudo apt clean        # to clear the cache wholesale
or
sudo mv /var/cache/apt/archives /var/cache/apt/archives-old      # to move the cache temporarily out of the default location
```
Either way, if the cache location is empty then it'll force it to download/fetch the information.

---

### Post by sacarde on 2020-02-21
deadflowr, I update with "apt update", and now it found a package to download and show me url

thank you very much

---

