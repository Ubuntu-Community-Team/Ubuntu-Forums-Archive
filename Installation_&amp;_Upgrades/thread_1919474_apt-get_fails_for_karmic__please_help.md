---
title: "apt-get fails for karmic  please help"
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by harrismh777 on 2012-02-02
hi, I still have a couple of machines on Karmic 9.10 and I would like to get some software from the archive (openjdk-6-jdk) and the command fails:

sudo apt-get install openjdk-6-jdk

I think its failing because Karmic is no longer supported... ?...  is there an archive for getting software for old releases?

thanks

:P

---

### Post by mikewhatever on 2012-02-03
You can get packages for unsupported releases by replacing the sources in /etc/apt/sources.list. For karmic, it would look like this:
> ## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-security main restricted universe multiverse

# Optional
#deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

Info source: [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by harrismh777 on 2012-03-01
Thank you :-k

The info you provided was absolutely correct, in theory... and I got a little further with it (it found the repositories),  but then the problem was that openjdk-6-jdk package does not exist on those repositories.

I finally just got fed up; I cleaned up my system and then upgraded it to 10.04 lucid.  

problem solved; mostly.  I had to tidy some things a bit (nothing big) and then I was able to get the openjdk-6-jdk package. (javac working well)

Thanks again for responding.   :popcorn:

---

