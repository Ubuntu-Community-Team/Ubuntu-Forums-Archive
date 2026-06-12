---
title: "How to Find New PPAs for v16.04"
date: 2016-09-20
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2016-09-20
Attempting to activate in "Other Software", PPAs for VirtualBox; SDK-Team; PipeLight; KdenLive; Webupd8team; Opera Browser ...

And Software Updater shows: "Requires Installation of Untrusted Packages", and clicking OK and Updater closes.

Apparently I have invalid PPAs for version 16.04. Where can I find the newer PPAs so I can input them into Updater?
(note: did a search but couldn't find anything specific)

Thanks!

---

### Post by #&amp;thj^% on 2016-09-20
For Pipelight 
 Try these commands from this [source]("http://pipelight.net/cms/install/installation-ubuntu.html"):
  ```
sudo add-apt-repository ppa:pipelight/stable
sudo apt-get update
sudo apt-get install --install-recommends pipelight-multi
sudo pipelight-plugin --update      


```
For Virtual box it is already in the Ubuntu Repos

For KdenLive
```
sudo add-apt-repository ppa:kdenlive/kdenlive-stable
sudo apt update
sudo apt install kdenlive

```

For SDK PPA
```
sudo add-apt-repository ppa:ubuntu-sdk-team/ppa
sudo apt update && sudo apt install ubuntu-sdk

```
For Opera see this: [http://www.ubuntuupdates.org/ppa/opera](http://www.ubuntuupdates.org/ppa/opera)
And i recall you had bit defender in there also.
[http://ubuntuguide.net/install-bitdefender-via-ppa-ubuntu](http://ubuntuguide.net/install-bitdefender-via-ppa-ubuntu)

---

### Post by Rick St. George on 2016-09-20
Thanks a Million ! ! !
This helps a lot.

Peace!

---

### Post by #&amp;thj^% on 2016-09-20
Glad it helped.
Cheers

---

