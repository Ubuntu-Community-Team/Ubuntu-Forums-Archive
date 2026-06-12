---
title: "bad repository"
date: 2020-01-21
forum: Installation &amp; Upgrades
---

### Post by josephfg on 2020-01-21
A while back, i tried to obtain a vid player from the miro site.  I was unable because there is no release file.  I installed "videos," which is working fine.  The problem is, now whenever I open the software updater it gives a message as follows:

```
Unable to download updates:
failed to refresh cache: E: The repository 'http://
ppa.launchpad.net/pcf/miro-releases/ubuntu disco Release'
does not have a Release file.
```

How do I get rid of this?  Thanks.

---

### Post by deadflowr on 2020-01-21
Either open Software and Updates  then go to Other Software and uncheck the miro ppa,
or run
```
sudo add-apt-repository -r ppa:pcf/miro-releases
sudo apt update
```
in a terminal.

---

### Post by CatKiller on 2020-01-21
```
sudo apt install ppa-purge
sudo ppa-purge ppa:pcf/miro-releases
```

---

### Post by guiverc on 2020-01-21
FYI:  19.04 reaches EOL on Thursday (23-Jan-2020) so *release-upgrade* asap  ([https://ubuntuforums.org/showthread.php?t=2434930&highlight=19.04](https://ubuntuforums.org/showthread.php?t=2434930&highlight=19.04))

If you open [http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/](http://ppa.launchpad.net/pcf/miro-releases/ubuntu/dists/) in a browser, you'll note the last release it supported was 12.10, so maybe shouldn't have been added to a later system (it's no longer maintained, could be a security risk as [https://launchpad.net/~pcf/+archive/ubuntu/miro-releases](https://launchpad.net/~pcf/+archive/ubuntu/miro-releases) shows it hasn't had much done since early 2013) thus I wouldn't have added it myself. 

It's best if you check PPA's before adding, as being 3rd party - the security is all on you.

---

### Post by josephfg on 2020-01-23
@deadflowr, thanks, although I could not find "Other Software" in Updates.  But the terminal commands did the trick.
@CatKiller, thanks for your input, I already used the other method (above) but it is interesting to know there are several ways to do things.
@guiverc, thank you for the advice.  I am pretty new to all this.

---

