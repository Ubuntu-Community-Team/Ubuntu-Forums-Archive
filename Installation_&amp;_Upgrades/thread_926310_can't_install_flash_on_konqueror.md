---
title: "can't install flash on konqueror"
date: 2008-09-21
forum: Installation &amp; Upgrades
---

### Post by randywilharm on 2008-09-21
I installed flash 9 on firefox via SYNAPTIC
It works on firefox (but youtube won't fullscreen)
Is there a special procedure to install
firefox on Konqueror or should it have
automatically been done already?

My goal is to be able to watch the vids I post on youtube 
fullscreen (big picture) and that's why I want to try
it with Konqueror as it just does'nt seem to
work with Firefox (I have the latest version).

Flash has a new version 10 available and i've tried every
trick I could to install it with no success
if anyone can see what i'm doing wrong please
tell me. I've enclosed .png of terminal readout.

I thank you for your time.
If you like pre-1970's scifi
movies check out [my youtube channel]("http://www.youtube.com/randywilharm")

---

### Post by Partyboi2 on 2008-09-22
> I installed flash 9 on firefox via SYNAPTIC
It works on firefox (but youtube won't fullscreen)
Is there a special procedure to install
firefox on Konqueror or should it have
automatically been done already?
try Settings>Configure Konqueror > Plugins> Scan for new plugins

---

### Post by kansasnoob on 2008-09-22
I recently found a .deb for Flash 10 Release Candidate that's worked very well for me in Hardy w/Firefox 3 and the newest Opera (I did however receive a message from someone saying that it wouldn't work in Feisty), but I've never used Konqueror.

[http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb](http://launchpadlibrarian.net/16766494/flashplugin-nonfree_10.0.1.218%2B10.0.0.569ubuntu1%7Eppa2_i386.deb)

Of course you'd first want to remove any (or all) previous versions of Flash:

```
sudo apt-get remove --purge flashplugin-nonfree
```

```
cd ~/.mozilla
rm flashplayer.xpt libflashplayer.so
```

I found that .deb here:

[http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/](http://tombuntu.com/index.php/2008/08/28/test-drive-adobe-flash-player-10-rc-in-ubuntu/)

I should also note that I'd previously followed the steps in this tutorial (but I'm not sure that's still necessary, or perhaps never was in Kubuntu):

[http://ubuntuforums.org/showpost.php?p=5587712&postcount=472](http://ubuntuforums.org/showpost.php?p=5587712&postcount=472)

---

### Post by randywilharm on 2008-09-22
> **Partyboi2 said:**
> try Settings>Configure Konqueror > Plugins> Scan for new plugins

hey thanks a lot!!
that's a great kitty you got for an avatar

---

### Post by randywilharm on 2008-09-22
hey thanks a lot-- that's one wealthy reply and i 
got a screenshot of it. I appreciate it ! Have a good one..

---

