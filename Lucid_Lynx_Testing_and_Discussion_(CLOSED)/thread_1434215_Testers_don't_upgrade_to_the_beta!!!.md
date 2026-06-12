---
title: "Testers don't upgrade to the beta!!!"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by swoll1980 on 2010-03-20
[It will break your desktop]("http://ubuntuforums.org/showthread.php?t=1434160"). I already screwed the pooch.

---

### Post by juancarlospaco on 2010-03-20
ok, if break will install another desktop :)

---

### Post by Phrea on 2010-03-20
All that panic... Have a coco. :popcorn:

---

### Post by madjr on 2010-03-20
hm i wish ubuntu would auto-backup

its why am always afraid of updating most things

---

### Post by swoll1980 on 2010-03-20
It's actually the first update after the beta that breaks it. so just don't update till it gets sorted.

---

### Post by juancarlospaco on 2010-03-20
Theres a SandBox for Upgrades on Repo.
*just a chroot and a little magic*

---

### Post by NightwishFan on 2010-03-20
Here is the bug report I posted on the issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

You can manage to log in by doing this:
When you get to a blank desktop press ctrl+alt+t, a terminal will pop up, type:
```
gnome-panel
```
leave terminal open.. then press alt+f2 and type:
```
nautilus
```

Don close terminal and it should be functional.

---

### Post by swoll1980 on 2010-03-20
The places links in the menu don't get opened by nautilus either they get opened by gwenview or something to that effect. Nautilus won't open at all it just crashes if I try to launch it. the devs are aware, so I guess I just wait, and see. This is why when I see those "is it stable enough to use? threads, and those over enthusiastic people are going on about how people should use the alpha because of how stable it is, I always warn them about the stuff that could happen.

---

### Post by Elfy on 2010-03-20
> **wgrant said:**
> We're working on fixing this right now. We expect that the main mirror will have the critical fixes in around two hours, but only time will tell, and some applications may need further fixes afterwards.

For now, do not upgrade.

> This is why when I see those "is it stable enough to use? threads, and those over enthusiastic people are going on about how people should use the alpha because of how stable it is, I always warn them about the stuff that could happen. yep +1 to that

---

### Post by madhi19 on 2010-03-20
> **NightwishFan said:**
> Here is the bug report I posted on the issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

You can manage to log in by doing this:
When you get to a blank desktop press ctrl+alt+t, a terminal will pop up, type:
```
gnome-panel
```
leave terminal open.. then press alt+f2 and type:
```
nautilus
```

Don close terminal and it should be functional.
And that might well be the most useful post of the year on this forum!

---

### Post by Khakilang on 2010-03-20
Well I always go for release and than updates. Safer and less frustrating that way.

---

### Post by Kenny_Strawn on 2010-03-20
The Beta is not what does it. It is a series of updates recently released for the Beta that introduce the bug. 

Use the [Lucid Beta 1 Live Image]('http://releases.ubuntu.com/10.04') and you will be fine. Just don't "update-manager -d" or "sudo apt-get upgrade"!

---

### Post by whiskeylover on 2010-03-20
> **NightwishFan said:**
> Here is the bug report I posted on the issue:
[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/542343)

You can manage to log in by doing this:
When you get to a blank desktop press ctrl+alt+t, a terminal will pop up, type:
```
gnome-panel
```leave terminal open.. then press alt+f2 and type:
```
nautilus
```Don close terminal and it should be functional.

or just type ```
gnome-panel &
``` and then you can close the terminal : )

---

### Post by FishRCynic on 2010-03-20
upgraded just fine here on amd64 - will check x86 in a bit

---

### Post by cecilpierce on 2010-03-20
just updated and gnome-panel is back to normal now.

---

### Post by wgrant on 2010-03-20
See the sticky thread -- the last updates fixing this will be on the main mirror in half an hour, except for those few users on sparc or armel who will have to wait a while longer.

---

### Post by 23meg on 2010-03-20
Closing this thread, as it's redundant with the sticky.

---

