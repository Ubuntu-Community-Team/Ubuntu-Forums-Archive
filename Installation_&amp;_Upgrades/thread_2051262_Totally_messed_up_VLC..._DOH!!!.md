---
title: "Totally messed up VLC... DOH!!!"
date: 2012-09-01
forum: Installation &amp; Upgrades
---

### Post by xdarkknight on 2012-09-01
ok, so I'm *aware* of computery things... not entirely savy, but somewhat able to comprehend tech talk.
I had VLC installed and working perfectly.  I saw that you can add the daily repository to my updates. So i did this, thinking that I may actually have a better experience by doing so.  As a result, I wasn't able to use VLC at all.  I'd click VLC to access it. Initially I waited and waited, but later realised that it wasn't going to open.  it may have been open in the alternate universe of my computer, but not the present, non-fictional universe that I live in.
I've left this for a while, not needing to use it.  But as I've moved permanently to the UK from the US and like to watch dvds on my laptop from either country, I kindof need a player that isn't dvd-racist.
I looked up "How do I completely uninstall VLC on Ubuntu" and found this website: [http://community.futuremark.com/forum/showthread.php?103409-Completely-removing-VLC-(Ubuntu](http://community.futuremark.com/forum/showthread.php?103409-Completely-removing-VLC-(Ubuntu))

I followed the directions. It seemed like it may have worked. so I restarted my system and tried re-installing VLC through the Software Center.  I was left with this dialog:

[COLOR="DarkSlateGray"]_**Package dependencies cannot be resolved**_
*This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.*
_The following packages have unmet dependencies:_
[I]vlc: Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but 2.0.3+git20120822+r347-0~r41~precise1 is to be installed
     Depends: libavcodec-extra-53 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libavutil-extra-51 (>= 4:0.8-1~) but 4:0.8.3ubuntu0.12.04.1 is to be installed
     Depends: libc6 (>= 2.15) but 2.15-0ubuntu10 is to be installed
     Depends: libfreetype6 (>= 2.2.1) but 2.4.8-1ubuntu2 is to be installed
     Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is to be installed
     Depends: libqtcore4 (>= 4:4.8.0) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libqtgui4 (>= 4:4.7.0~beta1) but 4:4.8.1-0ubuntu4.2 is to be installed
     Depends: libstdc++6 (>= 4.6) but 4.6.3-1ubuntu5 is to be installed
     Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu4 is to be installed[/I][/COLOR]

I'm out of good options.  I don't think I've killed my system, but I've definitely given it a bit of a run for it's money.  I know, knowledge can be useful.  A *little* knowledge can be dangerous.

Please Help!
xDK

---

### Post by Laiquendi on 2012-09-01
Check if you have not messed up the sources, sources settings.
Second point - you can try downloading missing dependencies from the internet.

---

### Post by xdarkknight on 2012-09-01
How would I know if I messed up the sources & where do I put the dependencies? Once downloaded, how do I apply the dependencies (meaning, do I need to "install" them to make them work?)

---

### Post by oldos2er on 2012-09-01
Is this the PPA you installed? [https://launchpad.net/~videolan/+archive/master-daily](https://launchpad.net/~videolan/+archive/master-daily)
Usually the "daily" or "nightly" versions of software are for testing by developers, they're not intended for end users.

If I were you I'd remove the daily repository, remove vlc and its config file: ```
sudo apt-get purge vlc

rm -r ~/.cache/vlc/

rm -r ~/.local/share/vlc/

rm -r ~/.config/vlc/
```

Update your repos and install vlc from the universe repo (the default version for 12.04) ```
sudo apt-get update && sudo apt-get install vlc
```

---

### Post by Vesa Paatero on 2012-09-01
... And if you still need to download some missing dependency manually, you can download specific packages from packages.ubuntu.com, and then use dpkg (or perhaps something apt-based) to install them.

Vesa

---

### Post by xdarkknight on 2012-09-02
WELL... I think I may have made some sort of progress...
I realised that it's not too difficult to install the dependencies and installed them. HOWEVER... now when I try to install vlc (using the terminal command), I get the following error:
[I] [COLOR="DarkSlateGray"] ** The following packages have unmet dependencies.**
 vlc : Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but 2.0.3+git20120822+r347-0~r41~precise1 is to be installed
       Recommends: vlc-plugin-notify (= 2.0.3-0ubuntu0.12.04.1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 2.0.3-0ubuntu0.12.04.1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
[/COLOR][/I]

So I install vlc-nox and it tells me:
*[COLOR="DarkSlateGray"] "vlc-nox is already the newest version." [/COLOR]*

So I figure that it should be fine to install these notify and pulse plugins, but it gives me this error:
[I][COLOR="DarkSlateGray"] The following packages have unmet dependencies.
 vlc-plugin-notify : Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but 2.0.3+git20120822+r347-0~r41~precise1 is to be installed
E: Unable to correct problems, you have held broken packages. 
[/COLOR][/I]
and
[I][COLOR="DarkSlateGray"] The following packages have unmet dependencies.
 vlc-plugin-pulse : Depends: vlc-nox (= 2.0.3-0ubuntu0.12.04.1) but 2.0.3+git20120822+r347-0~r41~precise1 is to be installed
E: Unable to correct problems, you have held broken packages. 
[/COLOR][/I]

I think this means I need to remove a package or 2, but I'm not sure if I need to uninstall vlc-nox or another one and I'm not sure of the commands for this.

Thanks for all the help thus far! I totally love Ubuntu for exactly this reason! good help. real people. not some windows-licker getting paid $120k/year to tell me to turn it off and on again.

Ubuntu Geeks, this is for you: YOU ROCK!

xDK

---

### Post by xdarkknight on 2012-09-02
I FIGURED IT OUT!!!  I had a broken package! (I know, this should have been obvious cause it told me that initially.)
VLC-nox was broken, so I used my black and white cane and tapped my way around, finally removing it and reinstalling it.

[I][COLOR="Sienna"]{For those interested, using the terminal, I decided to systematically uninstall and reinstall packages till it seemed to work as expected.
[LIST]
[*]To do this, I installed aptitude (sudo apt-get install aptitude) and searched for vlc-nox.
[*]Then, in aptitude, I selected VLC-nox for removal and executed the removal following the commands on the terminal.
[*]Then quit aptitude (too much going on, and I'm not used to the interface).
[*]Went back to the terminal input, and re-installed vlc-nox (sudo apt-get install vlc-nox).The install confirmation requested y/n, I selected y. And stuff started to happen! stuff I'd not seen before! Cool. 
[*]I then reinstalled VLC (sudo apt-get install vlc) and again: STUFF!
[/LIST]
I opened the program and all seems to be working the way it should!}[/COLOR][/I]
:guitar: {Rock and Roll Garth!}  {Rock and Roll Wayne!}:guitar:

All seems to be in order now and I'm happy!

Thanks to those who donated their intellect for the cause of my happiness.
xDK
:popcorn:

---

