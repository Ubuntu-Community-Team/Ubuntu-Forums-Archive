---
title: "Can't install/watch Flash Video, Divx and VLC in Gutsy..."
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by dESAI on 2007-12-31
Did a fresh install of Gutsy on a new HD for my dads PC. Everything was great and he's happy.

Did a fresh install of Gutsy on a new HD for myself...

Could not install VLC... error says something about conflicting software. 

Can't watch youtube or any site with flash video, when I try to download codecs the error is the same if not very similar. 

Can't watch divx on stage 6, same problem.

So I reinstalled everything again new on another new HD. Same problem...

Now I'm still very much a noob. But since I have reached a level where I can troubleshoot basic issues, I recommended Ubuntu to many people. I've even installed it on my dads PC, thats how impressed and confident I was. But this is just daft.

How can I not watch youtube?

My nerdy reputation is at stake here people! hehe ;)

I know other have had similar problems on the forums. Those posts either went nowhere or ended with me being completely lost in lines of code and giving up.

 I hope that someone out there can help :) 

Cheers!

Oh and all the best to all of you, your families and friends for the new year.

---

### Post by taurus on 2007-12-31
Sounds to me like there is a problem with your repos in /etc/apt/sources.list.  Bet you either have very little or no repos available for you to use.  

So, click System -> Administration -> Synaptic Package Manager -> Settings -> Repositories and put a check mark in front of all lines except the last one, Source code and the CDROM at the bottom window.  Close it and hit the Refresh button.  Now, type in vlc in the Search field and install it.

If you want media codecs, look for ubuntu-restricted-extras package.

---

### Post by ubuntu-freak on 2008-01-15
Try my how-to. Works perfect for me. There is a workaround for flash too.

[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

Nathan

---

### Post by Tiamats_Chosen on 2008-01-16
The installation worked for me. i can play my .avi .mkv. files but when i play anime all the Black lines are removed. is this a codec problem that can be fixed

---

### Post by wolfen69 on 2008-01-16
here's the flash fix for firefox:

if you installed flash-plugin, remove before downloading and installing the following flash file.

[http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb](http://mirror.ne.gov/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb)  then just click and install.

---

### Post by imran.jia on 2008-01-16
can you please help me?

From where did you got the softwares to install? give me the link.

I can't access net using my laptop, but I can download the sofware from outside.

How can I install the softwares?

I downloaded a gsteamer plugin and installed on ubuntu, and even then it doens't play the mp3 or other video files..

what should I do?

where can I get the plugins for Ubuntu. I want allths softwares of ubuntu.

---

### Post by ubuntu-freak on 2008-01-16
You need to follow this simple how-to 
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Nathan

---

