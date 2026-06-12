---
title: "Problem Istalling Pipelight in Xubuntu 16.04"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by marcus7702 on 2016-09-15
I have been attempting to install Pipelight on my Xubuntu 16.04 computer in order to access silverlight content on the Internet (eg. Netflix)

In doing so I used the following four terminal dialogs:

1) sudo add-apt-repository ppa : pipelight/stable
2) sudo apt-get update
3) sudo apt-get install --install-recommends pipelight-multi
4) sudo pipelight-plugin --update

I am never able to make it to the fourth step. after entering the third dialog the terminal window displays an end user license agreement and will not return to its usual state. I have tried everything I can think of. 





Thanks again

---

### Post by oldos2er on 2016-09-15
If that is the mscorefonts EULA, use the Tab key to highlight "Ok" then press Enter.

Much easier just to use Google Chrome though.

---

### Post by SeijiSensei on 2016-09-15
Or the beta release of Firefox with Widevine DRM from [this PPA](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next).  I'm using FF 49.0b8 and can access Netflix by turning on Widevine when prompted.  You'll only need to do this once.

---

### Post by deadflowr on 2016-09-15
> **SeijiSensei said:**
> Or the beta release of Firefox with Widevine DRM from [this PPA](https://launchpad.net/~mozillateam/+archive/ubuntu/firefox-next).  I'm using FF 49.0b8 and can access Netflix by turning on Widevine when prompted.  You'll only need to do this once.

Does firefox 49-beta still need a user agent switcher?
I know it took a little while for chrome to get the restriction lifted when widevine made it there, so...

---

### Post by SeijiSensei on 2016-09-15
Yes, it does.  I set up UAControl for this task when I was using Pipelight and forgot it was even running.  I haven't changed the User-Agent string in quite a while, and Netflix has yet to complain.  Right now I'm using
```
Mozilla/5.0 (Windows NT 10.0; rv:41.0) Gecko/20100101 Firefox/41.0
```
I tried changing it from 41.0 to 49.0 to match my browser's version, but Netflix balked and told me to install Silverlight.  When I changed it to 48.0, the current release version, I could watch videos again.  So if you're starting from scratch use 48.0 as the version number.

If I disable User-Agent spoofing for Netflix, I'm told to install Silverlight, so I guess spoofing is still required.

---

