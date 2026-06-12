---
title: "The following packages have unmet dependencies"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by kakaboeie on 2012-03-01
I get this message sometimes when trying to install software. Like just now, when trying to install VLC:

                                 The following packages have unmet dependencies: 
  
 vlc: Depends: vlc-nox (= 1.1.11-2build2) but 1.1.11-2build2 is to be installed 
      Depends: libaa1 (>= 1.4p5) but 1.4p5-38build1 is to be installed 
      Depends: libavcodec-extra-53 (>= 4:0.7-1) but it is not going to be installed 
      Depends: libavutil-extra-51 (>= 4:0.7-1) but it is not going to be installed 
      Depends: libc6 (>= 2.8) but 2.13-20ubuntu5 is to be installed 
      Depends: libfreetype6 (>= 2.2.1) but 2.4.4-2ubuntu1 is to be installed 
      Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.1-9ubuntu3 is to be installed 
      Depends: libqtcore4 (>= 4:4.7.0~beta1) but 4:4.7.4-0ubuntu8 is to be installed 
      Depends: libqtgui4 (>= 4:4.5.3) but 4:4.7.4-0ubuntu8 is to be installed 
      Depends: libsdl-image1.2 (>= 1.2.10) but 1.2.10-2.1 is to be installed 
      Depends: libsdl1.2debian (>= 1.2.10-1) but 1.2.14-6.1ubuntu4 is to be installed 
      Depends: libstdc++6 (>= 4.6) but 4.6.1-9ubuntu3 is to be installed 
      Depends: libva-x11-1 (> 1.0.12~) but it is not going to be installed 
      Depends: libxcb-randr0 (>= 1.1) but it is not going to be installed 
      Depends: libxcb-xv0 (>= 1.2) but it is not going to be installed 
      Depends: zlib1g (>= 1:1.2.3.3.dfsg) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
 
Now, I'm fairly sure I remember auto-upgrading/installing missing/auto-of-date software like this via the command line quite some time ago. I'd 'apt-get install' something and then add a flag that would make it auto-update/install the software/libraries for me if it found some outdated.

Can anyone refresh my memory?

---

### Post by Bucky Ball on 2012-03-01
Have you tried;

```
sudo apt-get install update
sudo apt-get install upgrade
sudo apt-get install vlc
```

... one command at a time?

---

### Post by kakaboeie on 2012-03-01
Thanks for your reply, that wasn't it though.

I was looking specifically for** apt-get -f install** . Not that it helped; it turned out I had to tick some extra software sources in Ubuntu Software Center -> Edit -> Software Sources and then do an apt-get update .

So yeah.. fixed! :)

---

### Post by Bucky Ball on 2012-03-02
Great. Please mark thread as 'Solved' from 'Thread Tools' at top right to help others. Enjoy! ;)

---

