---
title: "Ubuntu 14.04 Skype 4.3"
date: 2014-09-02
forum: Installation &amp; Upgrades
---

### Post by mishaparem on 2014-09-02
I had Skype 4.2 installed, and I was a happy camper until Skype decided "thou shall not login to skype on a version older than 4.3". I removed as much of skype (which was installed via the downloaded *.deb from Skype, and the Software Center), as I could, I don't remember the exact steps there, I just remember
```
mv ~/.Skype ~/.Skype.bak
```
There was some other step that I had to do. Anyhow, somehow I successfully removed every trace of Skype 4.2 from my system, but now when I went to install the 4.3 *.deb file (x64) it failed. The was some huge list of dependencies, I looked around and found
```
sudo apt-get install -f
```
That installed most of the dependencies, but there are 3 left: libqtgui4:i386, libqtwebkit4:i386, and libssl1.0.0:i386 I thought, "alright, lets try manually":
```
sudo apt-get install libqtgui4:i386
```
but I got
```
The following packages have unmet dependencies: libqtgui4:i386 : Depends: libfontconfig1:i386 (>= 2.9.0) but it is not going to be installed
                  Recommends: libcups2:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
I tried installing libfontconfig1:i386 which asked for fontconfig-config:i386:
```
sudo apt-get install libfontconfig1:i386
```
```
The following packages have unmet dependencies: libfontconfig1:i386 : Depends: fontconfig-config:i386 (= 2.11.0-0ubuntu4)
E: Unable to correct problems, you have held broken packages.
```
and then when I went to install fontconfig-config:i386, it up and decided to install a different package:
```
sudo apt-get install fontconfig-config:i386
```
```
Note, selecting 'fontconfig-config' instead of 'fontconfig-config:i386'
fontconfig-config is already the newest version.
```
So that's probably why I can't install libqtgui4:i386, right? If so, how do I fix it?

libqtwebkit4:i386 has more dependencies, and I did not feel the inclination to go through them manually. Apparently this is quite a common problem, and unfortunately the only two solved threads I found ended with "I formatted my PC and installed Skype first thing, and it worked". To me that's kind of unacceptable. The PC in question is my company PC that I work on, and we use Skype for communication.

Other things I've tried so far: software center, gdebi, dpkg, apt-get clean, apt-get update, apt-get upgrade

Any help is appreciated.

---

