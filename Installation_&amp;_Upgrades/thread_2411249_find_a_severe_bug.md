---
title: "find a severe bug"
date: 2019-01-27
forum: Installation &amp; Upgrades
---

### Post by zhaokun.ma on 2019-01-27
I use apt 1.2.26 in ubuntu 16.04. "apt update" carries out normally. However, there are ppas in /var/lib/apt/lists. All other sources exist in partial directory. And There are nothing in pkgcache.bin except ppas and installed softwares

---

### Post by TheFu on 2019-01-28
Better help would be possible with copy/pasted errors.  Please use text and code tags.

---

### Post by zhaokun.ma on 2019-01-29
```
Ign:18 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial/multiverse arm64 Packages
Ign:26 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial/universe arm64 Packages
Err:34 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-updates/main arm64 Packages
  404  Not Found
Ign:44 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-updates/multiverse arm64 Packages
Ign:50 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-updates/universe arm64 Packages
Err:56 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-backports/main arm64 Packages
  404  Not Found
Ign:63 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-backports/universe arm64 Packages
Err:71 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-security/main arm64 Packages
  404  Not Found
Ign:81 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-security/multiverse arm64 Packages
Ign:87 [http://mirrors.cn99.com/ubuntu](http://mirrors.cn99.com/ubuntu) xenial-security/universe arm64 Packages
Fetched 43.4 MB in 5s (8,239 kB/s)
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
E: Failed to fetch [http://mirrors.cn99.com/ubuntu/dists/xenial/main/binary-arm64/Packages](http://mirrors.cn99.com/ubuntu/dists/xenial/main/binary-arm64/Packages)  404  Not Found
E: Failed to fetch [http://mirrors.cn99.com/ubuntu/dists/xenial-updates/main/binary-arm64/Packages](http://mirrors.cn99.com/ubuntu/dists/xenial-updates/main/binary-arm64/Packages)  404  Not Found
E: Failed to fetch [http://mirrors.cn99.com/ubuntu/dists/xenial-backports/main/binary-arm64/Packages](http://mirrors.cn99.com/ubuntu/dists/xenial-backports/main/binary-arm64/Packages)  404  Not Found
E: Failed to fetch [http://mirrors.cn99.com/ubuntu/dists/xenial-security/main/binary-arm64/Packages](http://mirrors.cn99.com/ubuntu/dists/xenial-security/main/binary-arm64/Packages)  404  Not Found
E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by wildmanne39 on 2019-01-29
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by zhaokun.ma on 2019-01-29
I think if the following sentence contains some information?
```
AppStream cache update completed, but some metadata was ignored due to errors.
```

because all the files exist in /var/lib/apt/lists/partial

---

### Post by DuckHook on 2019-01-29
As wildmanne39 has already requested, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

Also please use the standard text and colours for ease of readability.

---

### Post by TheFu on 2019-01-30
[http://mirrors.163.com/ubuntu/dists/xenial-updates/main/](http://mirrors.163.com/ubuntu/dists/xenial-updates/main/) doesn't have any ARM repo that I see.  Only see amd64 and x86 versions.

BTW, I used mirrors.cn99.com, but that was redirected to the above DNS name.

At any point previous, did the ARM repos work/exist?  16.04 should have until 2021 before they are removed.

---

### Post by deadflowr on 2019-01-30
Indeed the main repo never has any arm packages, those are all in the ports repository.
(Universe and multiverse, et al do have arm packages, but main never does.
Which is why it's erring out.

/var/lib/apt/lists/partial is for the info still in transit, which too makes sense as since the info is erring out the stored info will just still in there until things get fixed. (Or at least that's my take on it)
You can get the fix from post 4 from here: [https://answers.launchpad.net/ubuntu/+source/apt/+question/661407]("https://answers.launchpad.net/ubuntu/+source/apt/+question/661407")

I think once you get the sources sussed out probably a good idea to wipeout the lists directory to allow it to start clean.
```
 sudo rm -rf /var/lib/apt/lists/*
sudo apt update
sudo apt full-upgrade
```

---

### Post by zhaokun.ma on 2019-02-01
thanks for your answer, i will try:popcorn:

---

