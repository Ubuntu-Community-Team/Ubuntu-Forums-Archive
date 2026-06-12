---
title: "Missing flash player error, when triggering from facebook via chromium"
date: 2014-08-29
forum: Installation &amp; Upgrades
---

### Post by Raj_Sanmugam on 2014-08-29
I upgraded to Ubuntu 14.04 lts. Everything seems to run smoothly except video viewing from facebook. I am using chromium browser.
Video plays fine from youtube and from firefox.

---

### Post by Dennis N on 2014-08-29
You may be missing the pepperflash plugin that Chromium now requires:

[http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html](http://www.webupd8.org/2014/01/pepper-flash-player-installer-for.html)

(The reason some video will play without it is that the video may be HTML5.)

---

### Post by vasa1 on 2014-08-29
Because the latest Chromium stable can no longer use the same plugin that Firefox uses. You'll need to install something called pepper flash from the repository. To do so, type **sudo apt-get install pepperflashplugin-nonfree** in a terminal and hit **enter** or search the software center for pepper flash!

(copy-paste from [http://ubuntuforums.org/showthread.php?t=2241765&p=13109947#post13109947](http://ubuntuforums.org/showthread.php?t=2241765&p=13109947#post13109947))

---

### Post by alopex38 on 2014-08-29
message to vasa 1 from Hippocrat

many thanks for your prompt help - sorted out my problem with iplayer/chromium

---

### Post by Raj_Sanmugam on 2014-08-29
Yes, installing pepperflash did the trick. 
Thanks for a quick reply Vasa and Denis.

---

