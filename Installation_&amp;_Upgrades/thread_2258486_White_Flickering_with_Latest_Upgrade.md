---
title: "White Flickering with Latest Upgrade"
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by False_Epiphany on 2014-12-28
Hey all,  My problem's pretty much what the title says. Upgraded to Ubuntu's latest version a couple hours ago, and now whenever I type anything in an application, the text and mouse cursor blink. White blocks flicker back and forth over random parts of the screen. Putting up with it for a couple minutes is merely annoying. Anything longer, and my eyes ache too much to even look at the screen. I'm posting this message from another computer, as my "upgraded" one is effectively unusable.   I've Googled for solutions and stumbled across [this](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/1314367), so at least my problem isn't unique to me, but no luck with any of the solutions that worked for other people. Turning on forced synchronization does nada. My graphics card is a Radeon HD 750G.  Thank you very much for any help!

---

### Post by MAFoElffen on 2014-12-28
Please install lshw (so you can post which video card revision it is and which graphics driver it is currently using) via this commend:
```

sudo apt-get install lshw

```
After that installs, then post the result of these
```

sudo lshw -numeric -class video
sudo lspci -vvnn | grep -i VGA
sudo lsmod
glxinfo -v
sudo vainfo
uname -a
lsb_release -a

```
Then post your /var/log/Xorg.0.log

Note that the bug you pointed to was a different graphics card (nVidia)...

---

