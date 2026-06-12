---
title: "Another Black Screen Bonanza!!"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by statistic on 2007-10-07
Alright So I began with a burned ISO live CD of Fiesty Fawn 7.0.4 and attempting to install it would give the loading splash and then just go black. So I rebooted in Safe Graphics mode and got the same problem. I then switched to a distribution CD and tried the same two things and got the same reactions. I showed no problems in a memtest. Here are my specs before I go any further:

Compaq Pressario 6310ca Notebook : [http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12139188-78299199-78308301-78308301-78308301-78867421-80299370.html](http://h10010.www1.hp.com/wwpc/ca/en/ho/WF06b/12139188-78299199-78308301-78308301-78308301-78867421-80299370.html)
it's that with the exception that it came with vista (shudders)

So someone suggested that I start by installing server version of Fiesty Fawn and then apt-get the thing into a desktop version. So I've done that successfully I believe because now it loads to the ubuntu loading splash before it goes black again and I am unable to do anything but hold the power button until it turns off. I am still able to run the command line if I go into recovery mode and get work done there.

I'm not terribly attatched to my current installation of non-functionality, all I can do is program, which is really all I need it for along with being able to FTP my projects around, so I don't mind starting from scratch.

Any insight into the issue would be greatly appreciated, thanks.

---

### Post by statistic on 2007-10-07
Well problem mostly solved, it turned out that I was not doing the final crucial command to making it work :P. After configuring my drivers using 
"dpkg-reconfigure xserver-xorg"
and setting my driver name to VESA I was rebooting to make it work instead of typing "startx". This is now believe is a file permissions problem, because I can boot the GUI from the command line with root access but not from start up. Does anyone know which folder I need to chmod to make this work?

---

