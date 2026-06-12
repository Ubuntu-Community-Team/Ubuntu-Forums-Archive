---
title: "no x and now?"
date: 2004-10-26
forum: Installation &amp; Upgrades
---

### Post by xale on 2004-10-26
hello i just finished installing my first ubuntu and i'm stuck without any x...

is there ubuntu-tool to configure it?

thankyou for your help!

a.l.e

---

### Post by jayclark on 2004-10-26
Ok, did you try to install the nvidia drivers/ati? If so you need to edit the XF86 config file. After you edit the XF86 config file type in nvidia-glx-config enable. And there you go.
If your not getting x on a clean install I guess take a look at you XF86 config file and make sure everythings right.

---

### Post by xale on 2004-10-26
tried ubuntu, wasn't able to detect my screen/graphic card, trashed?

it's what i should been doing!

sorry, but for an easy to use distribution, it is not an answer: "try to play with the config files".

and i did try with some normal values, but couldn't get anything better than a scrambled screen!

i give ubuntu a second try, i reinstall suse only to have a correct XF86config file, store it for ubuntu... and watch how it performs.

i don't need a flashy gui, but i'm not always ready to tweak with the config files! 

good luck ubuntu!

a.l.e

---

### Post by Rancoras on 2004-10-26
What video card are you using?

---

### Post by jayclark on 2004-10-26
What is your graphics card? Don't download the updates when it ask you to. Download them after it setups your computer. I had it not load X right when doing the updates while in setup. Not for sure why it did this. Also what type of computer do you have?

---

### Post by xale on 2004-10-26
sorry, it's an older notebook and i don't really know which graphic card is in it... 

it's nothing really special... something which worked almost out of the box with woody...

in about two hours suse will be installed, and i will know all the details...

and then two hours again to install ubuntu (probably tomorrow :-)

thank you for your help, but ubuntu is already erased and 11% of suse is already on the pc!

i would have loved to find like yast in ubuntu for configuring the system!

have a nice afternoon and thanks for you help!

a.l.e

---

### Post by jdong on 2004-10-26
If another distro worked (or you have a knoppix CD that works, etc) just copy over /etc/X11/XF86Config* to ubuntu.

---

### Post by FLeiXiuS on 2004-10-26
You can try running the following commands.  This time more theorly go by and check what is selected.  Also, if you can login as ROOT or some user via CLI, then I would recommend you printing us an error message.
```

cat /var/logs/XFree86.0.log |grep EE

```
 
Run these commands to reconfigure X.
```

X11 -configure
dpkg-reconfigure xserver-commom

```

---

### Post by xale on 2004-10-27
hello,

reinstalled suse, saved XF86config on the stick, reinstalled ubuntu, failed to mount the stick, copied the file by ssh, no ssh installed, installed ssh, copied the file by ssh, restarted gdm and it finally worked...

now i can start experimenting with ubuntu, but the first impression is still not that good. i have to install 3 computers and the specs of ubuntu seemed to be ok for that job. 

two glitches on old hardware are not very bad, but don't give a good impression either...

and scribus is not in the packages list... so bad... it was the main reason to put linux on those two computers!

though, i will make some tests with ubuntu, but i don't think i will choose it for that project.

thank you all for your help!

a.l.e

ps.: and no enlightenment, and no xfce...

---

### Post by Rancoras on 2004-10-27
Did you file a bug for the detection of your screen?  What was the difference between the config ubuntu created and the one from the other distro?

---

