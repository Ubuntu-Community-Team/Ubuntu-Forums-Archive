---
title: "Failed to load package list"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by fotcfanforums on 2015-07-24
For some reason I'm having a problem with installing updates. Every time I try I get this error: 

```
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
```

Any idea what the problem could be? It seems to be something to do with Chrome too, because when I tried using the software and updates option through the system settings, it says Google Chrome is an unauthorized program after I unchecked this repo on the other software section. 

I restarted the computer as well, and nothing changed. I am unable to install any updates because of this problem. 

Also I'm on Ubuntu 14.04

---

### Post by dino99 on 2015-07-24
i also often meet that 'i18n_Translation' error. As i understand that issue, it happen when the server is starting to update its list AND xapian-index Also start on your side.
That should not happen, but the design only use an index, and if that one is starting a modify process, then it is disturbed and fail.
I myself have reported that issue against 'apt' some times ago, but no fix nor assignment have been made; so we need to work around that issue:
- usuaaly reuploading the archive is enough; but sometimes switching the server (main) also help.
- wiping /var/apt/dist/archives/ also help (and/or using clean/autoclean/autoremove)

but its not a show stopper, so no worrying

---

### Post by huxley2 on 2015-07-24
I just got the exact same message. Yesterday I swapped around some disk space to increase my root partition so initially thought that that was the culprit. I'm using 14.04 amd64 with FireFox so doubt it's any fault with the browser.

Here's the message when I open package manager:

> E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.



---

### Post by dino99 on 2015-07-24
i also often meet that 'i18n_Translation' error. As i understand that issue, it happen when the server is starting to update its list AND xapian-index Also start on your side.
That should not happen, but the design only use an index, and if that one is starting a modify process, then it is disturbed and fail.
I myself have reported that issue against 'apt' some times ago, but no fix nor assignment have been made; so we need to work around that issue:
- usuaaly reuploading the archive is enough; but sometimes switching the server (main) also help.
- wiping /var/apt/dist/archives/ also help (and/or using clean/autoclean/autoremove)

but its not a show stopper, so no worrying

---

### Post by fotcfanforums on 2015-07-24
So, odd thing happened. The error icon is gone now. But I tried an update through the terminal, but it still shows the problem with those repo's or whatever. I'm not too worried about it, just annoying.

---

### Post by huxley2 on 2015-07-24
Can you use your package manager? As soon as I cancel the error message it automatically closes.

---

### Post by v3.xx on 2015-07-24
Seen this?

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Encountered+a+section+with+no+Package%3A+header+&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=Encountered+a+section+with+no+Package%3A+header+&sa=Search&cof=FORID:9)

---

### Post by bapoumba on 2015-07-24
Please have a look here : [http://ubuntuforums.org/showthread.php?t=2234757](http://ubuntuforums.org/showthread.php?t=2234757)

---

### Post by huxley2 on 2015-07-24
```
 sudo rm -rf /var/lib/apt/lists/*
```
```
sudo apt-get update && sudo apt-get upgrade
```

This left with some other error from steampowered.com, but after a restart, then update, autoclean & autoremove everything is working normally again.

---

### Post by v3.xx on 2015-07-24
Nice :)

don't forget

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

