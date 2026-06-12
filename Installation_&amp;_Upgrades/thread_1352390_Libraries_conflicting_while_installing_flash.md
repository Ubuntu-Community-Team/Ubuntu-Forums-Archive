---
title: "Libraries conflicting while installing flash"
date: 2009-12-11
forum: Installation &amp; Upgrades
---

### Post by tapas_mishra on 2009-12-11
I am getting some error while installing flash 
```

W: GPG error: http://ppa.launchpad.net hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 632D16BB0C713DA6
W: GPG error: http://ftp.debian.org etch Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B
W: GPG error: http://security.debian.org lenny/updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 9AA38DCD55BE302B

```I am not able to watch youtube videos due to it I have tried installing 
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb"))
but then even here I got error 
```

Error: Conflicts with the installed package 'flashplugin-installer'

```
then the following are the files which it shows to install

```

./
usr/
usr/lib/
usr/lib/xulrunner/
usr/lib/xulrunner/plugins/
usr/lib/xulrunner-addons/
usr/lib/xulrunner-addons/plugins/
usr/lib/mozilla/
usr/lib/mozilla/plugins/
usr/lib/iceape/
usr/lib/iceape/plugins/
usr/lib/iceweasel/
usr/lib/iceweasel/plugins/
usr/lib/firefox/
usr/lib/firefox/plugins/
usr/lib/midbrowser/
usr/lib/midbrowser/plugins/
usr/lib/adobe-flashplugin/
usr/lib/adobe-flashplugin/libflashplayer.so
usr/share/
usr/share/doc/
usr/share/doc/adobe-flashplugin/
usr/share/doc/adobe-flashplugin/copyright
usr/share/doc/adobe-flashplugin/changelog.Debian.gz

```

---

### Post by tapas_mishra on 2009-12-11
Well I just found a solution to the above problem it was solved by  removing swfdec-mozilla
```

aptitude remove swfdec-mozilla

```it is given here on this thread 

[http://ubuntuforums.org/showthread.php?t=1130307](http://ubuntuforums.org/showthread.php?t=1130307)

---

