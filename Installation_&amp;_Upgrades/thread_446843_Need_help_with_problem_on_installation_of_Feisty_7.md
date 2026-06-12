---
title: "Need help with problem on installation of Feisty 7.04"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by siefer132 on 2007-05-17
When i start up the live cd, it gets to the part where it loads everything, like the drivers, but then after that, it gives me a message saying something along the lines of " X was unable to detect a video card"or something like that, but it gives me an error message. When i try to use "sudo dpkg-reconfigure xserver-xorg", i set up the setting correctly( im assuming because they worked before, before i reformatted), and then after that it gives me a command line. What do i type in there to restart GDM? Ive tried all of the coomands i could think of.

-Thanks

---

### Post by siefer132 on 2007-05-17
If it helps, i have an ATI Radeon x1400 card...

---

### Post by siefer132 on 2007-05-17
anyone?:confused:

---

### Post by Ub1476 on 2007-05-17
Look here: [URL=[I]"https://bugs.launchpad.net/ubuntu/+s...ver/+bug/89853"]https://bugs.launchpad.net/ubuntu/+s...ver/
+bug/89853[/I][/URL]

And here: [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1"]https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1"]https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/103945/comments/1")

I have X1400 too, and had the same problem (I think?). The second link is the guide I used, but you might have to add the stuff under the monitor section, described in the first link.

---

### Post by siefer132 on 2007-05-17
the second link seems to explain how to do it, but the first one leads no where o.o, broken link i guess.

Thanks for posting this.:)

---

### Post by Ub1476 on 2007-05-17
Link corrected:
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/89853)

It simply just explain the bug/discussing it. You should add in your Monitor section (in xorg.conf) this: ```
HorizSync 36-52
VertRefresh 36-60
```

Or else gdm wont start. At least it didn't for me..

NOTE: When you have installed and enable the ATI driver, manually add your resolution to xorg.conf, or it wont work. Also it's much faster doing it that way.:biggrin:

---

