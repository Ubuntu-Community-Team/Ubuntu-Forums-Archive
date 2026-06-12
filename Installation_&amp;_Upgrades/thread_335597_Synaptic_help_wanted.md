---
title: "Synaptic help wanted"
date: 2007-01-10
forum: Installation &amp; Upgrades
---

### Post by mkolby on 2007-01-10
Hi everyone

Having just installed Ubuntu yesterday, I'm already having trouble...

My installation is Ubuntu 6.06 LTS by the way.

First, I found out that the version of Firefox after the installation wasn't the newest one. I updated everything, but Firefox wasn't updated. Also the "Check for updates" in "Help" in the Firefox menu was greyed out, and as such didn't work. 

I downloaded Firefox 2, but there's no installation help available for Linux users (very strange if you ask me). I don't know what to do...

Anyway, I continued using the old firefox, but wanted to install RealPlayer, as I found out I couldn't see any kind of streaming video. A bit annoying that those kinds of plugins do not come standard or as an update. However, after downloading RealPlayer 10 Gold, I don't know  what to do with the file. Usually in Windows, a doubble-click does the trick, but now... nothing.

What to do?? I looked through the forum posts, finding out how to get Synaptic to get packages containing these thing I wanted. Unfortunately, I must have made a mistake, because it doesn't work.

Error message: Critical error. check rights and errors in /etc/apt/sources.list. 

I did this, and think there is a mistake in one of the lines. I think I missed a letter when copying from what the forum said. Unfortunately, I can't correct it and save it on top, because apparently I don't have the rights.

How do I correct whatever I did, replace the file or reinstall Synaptic? Why doesn't anything happen when I try to run the installation file for RealPlayer?

---

### Post by tombs on 2007-01-10
About RealPlayer:
[http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux', 'install_instructions', '570','400','scrollbars=1,resizable=1');]("http://http://www.real.com/moreinfo/playerplus_install.html?system=linux&pageid=unagi.8083677&pageregion=install_instructions&src=linux&pcode=rn&opage=linux', 'install_instructions', '570','400','scrollbars=1,resizable=1');")
There is nothing difficult.
About Firefox, try to edit yor sources.list as root:
sudo nano(or any other editor) /etc/apt/sources.list

---

### Post by d3v1ant_0n3 on 2007-01-10
[ Installing firefox 2 in dapper](http://ubuntuforums.org/showthread.php?t=330386)

---

### Post by d3dtn01 on 2007-01-10
You seem to have a few separate issues. As far as using Synaptic, are you logged in as a user with admin rights? If so, you shouldn't have any rights issues.

As far as installing RealPlayer, there is a link below the "Download RealPlayer" button on the download page ([http://www.real.com/linux/)](http://www.real.com/linux/)). The directions are rather simple to follow.

---

### Post by mkolby on 2007-01-10
As for the problem with Synaptic, I solved it by following a previous thread. 

I still need to get Firefox 2 and the plugins. I am going to try to get them and FF by installing Automatix, as that seems easier for a beginner.

I'm not sure I have all rights, eventhough I am the only user. How does one check?

---

### Post by d3dtn01 on 2007-01-10
As previously mentioned, you need to edit the sources.list file as root. So, at the terminal, type:

```
sudo gedit /etc/apt/sources.list
```

You'll be prompted for your password, then gedit should open up and you can modify the sources file. Then you should be able to go to Synaptic and find the package(s) that you're looking for.

---

### Post by mkolby on 2007-01-10
Thanks, I've done that. It works now. 

I still want Firefox 2, and it's not in Automatix. Can you update Automatix, or should I install manually, as this link says: [http://ubuntuforums.org/showthread.php?t=330386](http://ubuntuforums.org/showthread.php?t=330386)

Two things though:

The Totem video plugin doesn't seem to work with Firefox 2.x. You may want to install package mozilla-mplayer instead before you start.

You need the package libstdc++5 installed.

What does this mean? How do I do it, or should I ignore it?

---

### Post by d3dtn01 on 2007-01-10
I don't use Automatix, so I can't really speak to that. Have you tried the direction on this site:

[http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/]("http://everythingelse.wordpress.com/2006/07/15/howto-install-firefox-20-bon-echo-in-ubuntu/")

---

### Post by mkolby on 2007-01-10
Thx, that did it!

---

### Post by d3dtn01 on 2007-01-10
Hm. Are you in the correct directly when you try to run the script? In other words, are you in the directory where the script is stored?

Perhaps you need to put a "sudo" in front of "./firefox2.sh". So try:

```
sudo ./firefox2sh
```

---

