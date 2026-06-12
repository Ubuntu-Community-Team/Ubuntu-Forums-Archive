---
title: "Cannot Upgrade From 23.04 to 23.10"
date: 2023-11-06
forum: Installation &amp; Upgrades
---

### Post by mrkeef on 2023-11-06
Whenever I try to upgrade from 23.04 to 23.10 I get this error:
Error during update

> A problem occurred during the update. This is usually some sort of
network problem, please check your network connection and retry.

I don't have an internet problem. In fact, the upgrade process downloads stuff before it gets to this point.

I have tried both "Software Updater" and the CLI command sudo do-release-upgrade (with -d and -c ,not both at the same time)

---

### Post by Rubi1200 on 2023-11-06
Was this the first upgrade attempt? Are there other error messages?

Please show us your sources list:

```
cat /etc/apt/sources.list
```

---

### Post by mrkeef on 2023-11-07
Sources list:
> cat /etc/apt/sources.list
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar main restricted
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-updates main restricted
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar universe
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-updates universe
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar multiverse
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-updates multiverse
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-backports main restricted universe multiverse
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-security main restricted
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-security universe
deb [https://ubuntu.mirror.digitalpacific.com.au/archive/](https://ubuntu.mirror.digitalpacific.com.au/archive/) lunar-security multiverse

> When I run the upgrade I get thismessage about the vivaldi repo even though I have disabled it:
Ign [https://repo.vivaldi.com/archive/deb](https://repo.vivaldi.com/archive/deb) stable InRelease                                                                                                                                    
Get:1 [https://repo.vivaldi.com/archive/deb](https://repo.vivaldi.com/archive/deb) stable Release [3,840 B]                                                                                                                          
Get:2 [https://repo.vivaldi.com/archive/deb](https://repo.vivaldi.com/archive/deb) stable Release.gpg [833 B]                                                                                                                        
Err [https://repo.vivaldi.com/archive/deb](https://repo.vivaldi.com/archive/deb) stable Release.gpg                                                                                                                                  
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 62993C724218647E  

---

### Post by MAFoElffen on 2023-11-07
Please show the results of this posted within CODE Tags:
```

ls /etc/apt/sources.list.d/* | xargs -I {} sh -c "grep . {}" | grep -v "#"

```

---

### Post by mrkeef on 2023-11-07
deb [signed-by=/usr/share/keyrings/vivaldi-browser.gpg arch=amd64] [https://repo.vivaldi.com/archive/deb/](https://repo.vivaldi.com/archive/deb/) stable main
deb [signed-by=/usr/share/keyrings/vivaldi-browser.gpg arch=amd64] [https://repo.vivaldi.com/archive/deb/](https://repo.vivaldi.com/archive/deb/) stable main
deb [signed-by=/usr/share/keyrings/vivaldi-browser.gpg arch=amd64] [https://repo.vivaldi.com/archive/deb/](https://repo.vivaldi.com/archive/deb/) stable main
Types: deb
URIs: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)
Suites: kinetic
Components: main
Architectures: amd64 i386
Signed-By: /etc/apt/keyrings/winehq-archive.key
Enabled: no
Types: deb
URIs: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)
Suites: kinetic
Components: main
Architectures: amd64 i386
Signed-By: /etc/apt/keyrings/winehq-archive.key
Enabled: no
Types: deb
URIs: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)
Suites: lunar
Components: main
Architectures: amd64 i386
Signed-By: /etc/apt/keyrings/winehq-archive.key
Enabled: no
Types: deb
URIs: [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu)
Suites: lunar
Components: main
Architectures: amd64 i386
Signed-By: /etc/apt/keyrings/winehq-archive.key
Enabled: no

---

### Post by ActionParsnip on 2023-11-07
[https://forum.vivaldi.net/topic/82801/pub-key-missing/5](https://forum.vivaldi.net/topic/82801/pub-key-missing/5)

---

### Post by ActionParsnip on 2023-11-07
```

wget -qO- https://repo.vivaldi.com/archive/linux_signing_key.pub | gpg --dearmor | sudo dd of=/usr/share/keyrings/vivaldi-browser.gpg

```

Source:
[https://forum.vivaldi.net/topic/82801/pub-key-missing/10](https://forum.vivaldi.net/topic/82801/pub-key-missing/10)

---

### Post by mrkeef on 2023-11-07
Thank you guys! That did the trick.
I really appreciate you taking the time to help me,
Keith

---

### Post by MAFoElffen on 2023-11-07
That fixed "that" error, but you potentially have more errors to prevent.

Number 1 rule for PPA and Upgrading a release version is to disable your PPA's "before" you attempt a go-release-upgrade... From the output which I asked for, you still have many PPA, and external repo's to disable before you are ready for that...

The easiest way to do that, is to start up the "Software & Updates" app > Software tab > write down all the ones that are checked (currently)... Important. After you do that, uncheck them all.

Do your release upgrade.

After it is through... Start That app back up, and check those written down checkboxes again. Close the app.

Then open a terminal...
```

sudo apt update ## [COLOR=#ff0000]<--- Do not do the second command if you have errors with this[/COLOR]
sudo apt upgrade

```
Check the output for errors... Why? >>> Because some PPA's and repo's may end at a certain release version, like where you were at before the release upgrade. 

If you get an error with a message something like: "missing release file"... Then that is the case. Go back to that app, and uncheck the box for whatever that was. Wash, rinse, repeat until you have no errors.

The second command will see the release is newer, ad update the packages from that PPA or Repo.

---

