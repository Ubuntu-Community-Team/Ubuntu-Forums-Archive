---
title: "How to keep my programs when updating (and other questions)"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by skytreader on 2010-06-14
Hi. I'm still at Karmic, planning to upgrade to Lucid. However, what keeps me from doing so are the programs I've installed.

Is there a way to upgrade and still keep my installed programs? It'd take a hellish lot of time to install them again. I thought that upgrading via Upgrade Manager might be the answer but none of the local Linux (Ubuntu) users could verify as they never tried. It seems that they always "wipe everything and install".

In any case, they discourage me to do so. Upgrading via Update Manager always seem to fail (and I'd get my machine corrupted) because internet connection here is slow (my *broadband* peaks at 50kbps, averaging at 36-45kbps...slow indeed) and most likely breaks for something as strenuous as upgrading an OS.

Also some other questions...

1) Is the matrix code rain wallpaper still at Lucid (GLMatrix, it's called)? If not, can I download it anywhere?
2) Is the outer space wallpaper still at Lucid (the one that changes every now and then, ala some GMail themes)? Is there a way to create my own slideshow wallpaper?

Much thanks everyone...

---

### Post by rhy7s on 2010-06-14
You realise most of the packages will be upgraded so it'll take some time regardless? Maybe you could aptitude install the output from [http://ubuntuforums.org/showpost.php?p=2773031&postcount=6](http://ubuntuforums.org/showpost.php?p=2773031&postcount=6) after a clean install (reusing your home folder to keep config files). edit: here's another page on how to generate this list: [http://superuser.com/questions/6338/how-do-you-track-which-packages-were-installed-on-ubuntu-linux/6932#6932](http://superuser.com/questions/6338/how-do-you-track-which-packages-were-installed-on-ubuntu-linux/6932#6932)

---

### Post by garvinrick4 on 2010-06-14
> **skytreader said:**
> Hi. I'm still at Karmic, planning to upgrade to Lucid. However, what keeps me from doing so are the programs I've installed.

Is there a way to upgrade and still keep my installed programs? It'd take a hellish lot of time to install them again. I thought that upgrading via Upgrade Manager might be the answer but none of the local Linux (Ubuntu) users could verify as they never tried. It seems that they always "wipe everything and install".

In any case, they discourage me to do so. Upgrading via Update Manager always seem to fail (and I'd get my machine corrupted) because internet connection here is slow (my *broadband* peaks at 50kbps, averaging at 36-45kbps...slow indeed) and most likely breaks for something as strenuous as upgrading an OS.

Also some other questions...

1) Is the matrix code rain wallpaper still at Lucid (GLMatrix, it's called)? If not, can I download it anywhere?
2) Is the outer space wallpaper still at Lucid (the one that changes every now and then, ala some GMail themes)? Is there a way to create my own slideshow wallpaper?

Much thanks everyone...
At 50kkbps you are going to crawl in upgrading your system from karmic to lucid, I have upgraded a version quite often and do not have any problems. Keeps all your System Settings the same 100% of time but you are going to be slow like 56k modem slow but I remember when the 300 to 1200 baud modem came out which was 20 times slower than yours and I thought I was fast at the time. So fast is relative if you want to think of it that way. At 56k might as well think relative, cause you will take a bit of time to upgrade. I will give you the code to do it in terminal in one swoop. Here ye go.
                                 

```
sudo sed -i 's/karmic/lucid/g' [/etc/apt/sources.list]("file:///media/etc/apt/sources.list") && sudo aptitude update && sudo aptitude dist-upgrade
```Copy and Paste and take a nap or stare at the terminal for a while.

---

