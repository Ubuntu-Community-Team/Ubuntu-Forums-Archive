---
title: "Cached packages (debs)"
date: 2013-10-26
forum: Installation &amp; Upgrades
---

### Post by mbnoimi on 2013-10-26
Howdy,

I'm using Ubuntu since years so I've about 30GB of cached packages because I've limited quota of WiMAX Internet connection so I wonder how can I get rid of old packages without removing the unused packages?

Exmaple: I've the following firefox debs while I just want the recent version only:
```
firefox_16.0.2+build1-0ubuntu0.12.04.1_amd64.deb  firefox_18.0+build1-0ubuntu0.12.04.3_amd64.deb    firefox_21.0+build2-0ubuntu0.12.10.2_amd64.deb     firefox_24.0+build1-0ubuntu0.13.04.1_amd64.deb
firefox_17.0.1+build1-0ubuntu0.12.04.1_amd64.deb  firefox_19.0.2+build1-0ubuntu0.12.10.1_amd64.deb  firefox_22.0+build2-0ubuntu0.12.10.1_amd64.deb     firefox_24.0+build1-0ubuntu0.13.04.1_amd64.deb.ug_
firefox_17.0+build2-0ubuntu0.12.04.1_amd64.deb    firefox_19.0+build1-0ubuntu0.12.10.1_amd64.deb    firefox_22.0+build2-0ubuntu0.12.10.2_amd64.deb
firefox_18.0.1+build1-0ubuntu0.12.10.1_amd64.deb  firefox_19.0+build1-0ubuntu0.12.10.2_amd64.deb    firefox_23.0+build2-0ubuntu0.13.04.1_amd64.deb
firefox_18.0.2+build1-0ubuntu0.12.10.1_amd64.deb  firefox_20.0+build1-0ubuntu0.12.10.3_amd64.deb    firefox_24.0+build1-0ubuntu0.13.04.1_amd64(0).deb

```

P.S. I always sync the path of cached packages (/var/cache/apt/archives/) because Ubuntu always delete the old and the unused packages!!!

---

### Post by ian-weisser on 2013-10-26
sudo apt-get autoclean

Excerpt from the apt-get man page:
```
       autoclean
           Like clean, autoclean clears out the local repository of retrieved
           package files. The difference is that it only removes package files
           that can no longer be downloaded, and are largely useless. This
           allows a cache to be maintained over a long period without it
           growing out of control. The configuration option
           APT::Clean-Installed will prevent installed packages from being
           erased if it is set to off.
```

---

### Post by mbnoimi on 2013-10-26
>  sudo apt-get autoclean
I tried it before; It removes some packages which I need them for example it removes amarok_2.7.1-0ubuntu0.1~ubuntu13.04~ppa1_amd64.deb which is needed and already used!

---

### Post by aperomsik on 2013-10-26
> **mbnoimi said:**
> I tried it before; It removes some packages which I need them for example it removes amarok_2.7.1-0ubuntu0.1~ubuntu13.04~ppa1_amd64.deb which is needed and already used!

If it is already installed, why do you need to keep the .deb file? 

If you are thinking of copying the same deb file for installing on another machine, you might take a look at apt-cacher-ng. It serves as a caching proxy for the ubuntu servers, and its cleanup rules might be more consistent with what you are thinking about.

---

### Post by mbnoimi on 2013-10-26
> If it is already installed, why do you need to keep the .deb file? 
I've  other PCs needs theses debs.

> you might take a look at apt-cacher-ng. It serves as a caching proxy for the ubuntu servers, and its cleanup rules might be more consistent with what you are thinking about. 
It may what I'm looking for, but is there any GUI interface to configure it?

---

### Post by aperomsik on 2013-10-26
> **mbnoimi said:**
> I've  other PCs needs theses debs.


It may what I'm looking for, but is there any GUI interface to configure it?

I'm not aware of one, but the config file is not rocket science.

---

### Post by mbnoimi on 2013-12-25
> I'm not aware of one, but the config file is not rocket science. 
Sorry for delaying this thread :(

I tested apt-cacher-ng and I found it very awesome but it works in case all PCs connecting together, In my case I've many PCs don't connect together so I sync the cached deb manually which make the size too big.

Do you've any solution to get rid of these unneeded packages?

---

### Post by ian-weisser on 2013-12-25
> **mbnoimi said:**
> I tried it before; It removes some packages which I need them for example it removes amarok_2.7.1-0ubuntu0.1~ubuntu13.04~ppa1_amd64.deb which is needed and already used!

If you don't trust autoclean, then you must clean your cache manually.
You should probably be upgrading from 13.04 soon anyway.

---

