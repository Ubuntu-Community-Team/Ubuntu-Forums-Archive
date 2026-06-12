---
title: "Nvidia Problems on a Gutsy clean install"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by fain on 2007-10-21
I've been at this all night......

I decided to do a fresh install of gutsy. i got in, every thing looked great. Until i tried to play a video.
so i did some research and found that it is a bug in nvidias driver 100.14.19. [clicky]("http://www.nvnews.net/vbulletin/showthread.php?t=98852&page=3") that causes video playback to be corrupt and on my system pink and green. 
ok so i decide to upgrade to the 100.14.23 driver they have released. install goes good but wait a minute, whats this "low res mode????"  wtf i just upgraded? Ok so i uninstall that and try reinstalling the repo driver. nope still low res mode.

I did every thing. i even reinstalled the whole os again and installed the 100.14.23 driver before i enabled the restricted driver in the repo. 
sudo /etc/init.d/gdm start
yay im in!!!!!!!! \\:D/
i get done installing my soft ware configuring it and i need to reboot now.
doh!!!! low res mode, again WHY!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ](*,)
i dont understand, it was working before????? :confused:
Now im back a square one i dont wanna re-install again :cry:

Ive found a few other posts with something similer to my problem but none helped
[http://ubuntuforums.org/showthread.php?t=578288&page=2]("http://ubuntuforums.org/showthread.php?t=578288&page=2")
and
[http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383]("http://ubuntuforums.org/showthread.php?p=3575383&posted=1#post3575383")
to name a couple.

I've got to go to bed now but any help would be greatly appreciated ill get back to you tomorrow.

---

### Post by fain on 2007-10-21
I usually like doing things the manual way but i couldnt wait on this one so i decided to try the envy script [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html"). it worked!!!! thanks Alberto, i still would like to know what was wrong though. It even gave me the 100.14.19 driver and my video's works??????
i don't understand.

---

