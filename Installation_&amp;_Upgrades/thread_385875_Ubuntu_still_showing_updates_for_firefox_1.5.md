---
title: "Ubuntu still showing updates for firefox 1.5"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by nolonx on 2007-03-16
Hello,

I've installed firefox 2.0.0.2 under dapper following the instructions at:

[https://help.ubuntu.com/community/FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion")

but the ubuntu updater is still notifying me of firefox 1.5 updates... I know that it is still installed on my system, but I thought that making FF2.0 the default browser by using these lines would also remove the FF1.5 updates:

```
 # First, /usr/bin/firefox
 sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/firefox
 # Then, /usr/bin/mozilla-firefox, used as the default gnome browser
 sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox
 sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

providing that it seems a bad idea to remove FF1.5 from synaptic, how do I solve this? I'm quite tired of that baloon on the upper right corner of the screen popping up every time I turn on the pc :D

Thanks

P.S: the script at [http://www.psychocats.net/ubuntu/firefox]("http://www.psychocats.net/ubuntu/firefox") didnt work for me (i cant remember why as I ran it weeks ago)
PP.S: unfortunately I cant upgrade to edgy (which has FF2.0 by default) because this is my work computer and I cannot loose the time needed to upgrade.

---

