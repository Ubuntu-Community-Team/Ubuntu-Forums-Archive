---
title: "is the mainline PPA abandoned?"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by akos.maroy on 2010-02-15
Hi,

I'm looking at the mainline kernel PPA, and it seems to be somewhat abandoned. for example, the repository sources don't even contain a karmic section, let alone lucid: [http://ppa.launchpad.net/kernel-ppa/ubuntu/](http://ppa.launchpad.net/kernel-ppa/ubuntu/)

my main concern is, I'd like to rebuild the most recent kernel package with a custom patch on lucid, but without a source repository, I can't do apt-get source, and thus I can't get the .dsc file for the pacakge..

how / where could I do that?

---

### Post by anaconda on 2010-02-15
Just wait a few hours, and it will propably be working again....

The servers can be down sometimes. 

It happens.

---

### Post by akos.maroy on 2010-02-15
> **anaconda said:**
> Just wait a few hours, and it will propably be working again....

The servers can be down sometimes. 

It happens.

well, the server isn't down - it's just that there's no repository for karmic or lucid, thus one gets a 404 Not found for the Packages.gz file when updating the sources, after adding the mainline PPA source

---

### Post by bruno9779 on 2010-02-15
why don't you apt-get it?

```
sudo apt-get install linux-source-2.6.17 kernel-package libncurses5-dev fakeroot
```

from:
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

---

### Post by akos.maroy on 2010-02-15
> **bruno9779 said:**
> why don't you apt-get it?

```
sudo apt-get install linux-source-2.6.17 kernel-package libncurses5-dev fakeroot
```

from:
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

bacause I need a mainline kernel under lucid. do you know of a working apt-get source that has it? tell me :)

---

