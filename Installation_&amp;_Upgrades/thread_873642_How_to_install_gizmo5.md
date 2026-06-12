---
title: "How to install gizmo5 ?"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by gotix on 2008-07-29
I would like to install Gizmo ([http://gizmo5.com/pc/](http://gizmo5.com/pc/))
I got the gizmo-project_3.1.0.79_libstdc++6_i386.deb file and now I don't know what to do with it.
thanks

---

### Post by Potatoj316 on 2008-07-29
view it in nautilus and double click on it

---

### Post by nbayiha on 2008-07-30
[http://gizmo5.com/pc/download/linux/](http://gizmo5.com/pc/download/linux/)
Here is the deb package

---

### Post by layx on 2008-09-25
Hi!

On the [http://gizmo5.com/pc/download/linux/](http://gizmo5.com/pc/download/linux/) web page, they recommend bonjour at [http://gizmo5.com/pc/download/bonjour/](http://gizmo5.com/pc/download/bonjour/). The .deb install fail (I made it whit other .deb before), and nothing is write in the terminal. There is no tar.gz either, like suggested. Any solution?
Scuse my so basic english
Ubuntly, layx

---

### Post by layx on 2008-09-25
Hi!

On the [http://gizmo5.com/pc/download/linux/](http://gizmo5.com/pc/download/linux/) web page, they recommend bonjour at [http://gizmo5.com/pc/download/bonjour/](http://gizmo5.com/pc/download/bonjour/). The .deb install fail (I made it whit other .deb before), and nothing is write in the terminal. There is no tar.gz either, like suggested.
Any solution?
Scuse my so basic english
Ubuntly, layx

---

### Post by Sonah on 2008-10-01
anybody know how to install gizmo5 in ubuntu?
[http://gizmo5.com/pc/download/linux/](http://gizmo5.com/pc/download/linux/)


they also Recommend Bonjour?
[http://gizmo5.com/pc/download/bonjour/](http://gizmo5.com/pc/download/bonjour/)


please Help ..

---

### Post by br4d on 2008-12-22
Sonah,

I'm a newbie too. AFAIK: there is a warning on the Gizmo's site not to install Bonjour if u have avahi.

My standard installation from hardy has installed avahi by default. Also I just install the Gizmo deb-package.

Hope it helps,
Brad

---

### Post by Stoneface on 2009-07-19
There are two .deb packages @ [http://gizmo5.com/pc/download/linux/](http://gizmo5.com/pc/download/linux/) .  libstdc++5: 3.1.0.79 and  libstdc++6: 3.1.0.79 . Which one is recommended? Second question, why is there no Gizmo to download using aptitude? A good alternative as Skype does not work well (in my experience so far) under Ubuntu. Gizmo5 is a nice alternative, isn't it? Furthermore, .deb file packages don't get updated automatically, which is a shame as I try to be as lazy as I can ;-)

---

### Post by kiridude on 2009-07-20
Since I see alot of people viewing this thread and that this thread really doesn't give any answers, here's how to install Gizmo:

- download the .deb file
- right click on the downloaded package and then click "open with Gdebi package installer."
- follow the directions and it will automatically be placed under places > internet.

---

### Post by greybeard95a on 2009-08-12
Hey you all,

I can't actually find a package for gizmo5.

Yeah, I see this other stuff on their download page.  But links to actually download the gizmo5 software are missing.  It is also really strange that I can't find it in either Debian or Ubuntu repositories.  (I would swear I had installed it previously.)

What gives?

---

### Post by kiridude on 2009-08-15
It's on this [page]("http://gizmo5.com/pc/download/linux/"). I just checked and its there.

If you're using Ubuntu, download the Debian packages (as I said in previous post).

---

### Post by greybeard95a on 2009-08-15
Not showing up in my browser.  I even opened up the web page source and searched for deb.  I see links for libstdc++ (?) packages but not for the gizmo .deb.

---

### Post by kiridude on 2009-08-16
libstdc is what you want.

On the Linux download page there are 4 categories:
- Linspire
- Debian
- Rpm
- Binary tarball

Here, you want the Debian section. 

Under the Debian logo, you will see, "Gizmo DEB Install Package" and two possibilities: libstdc++5 and libstdc++6. I could not find the difference between the two, so just downloaded 6. When you download the package, you will see that it is a .deb file.

---

### Post by The JESTer on 2009-08-31
Gizmo 5 is working great for me on jaunty. They have a new website from what I first used. Are you going to [www.gizmo5.com?](www.gizmo5.com?) Here you should click on "download for desktop". This should take you to the download page. Here you should be able to click on "Linux Download." Here, under debian I clicked on "libstdc++6: 3.1.0.79." This downloaded it to my desktop, where I clicked on it and jaunty atomatically installed it. After that, once I got PulseAuido working correctly, I configured Gizmo, "Gizmo/preferences/audio," setting it to ALSA under "sound system" and to my sound card (not default) under "Current Sound Sytem: ALSA." I was then able to make calls with it and have had no problems.[URL="http://download.gizmo5.com/GizmoDownload/gizmo-project_3.1.0.79_libstdc++6_i386.deb"] 
[/URL]

---

### Post by amsonia on 2009-09-18
A far easier way to install Gizmo5 is to add the medibuntu repository and then 
sudo apt-get install gizmo5.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by rexmo on 2009-11-29
Hey google!
What did you do with .deb packages?!

This seems pretty evil to me...

---

### Post by emooney on 2009-12-28
I'm using Ubuntu 9.10 and was getting an error when trying to install libstdc++**5**: 3.1.0.79. So I tried libstdc++**6**: 3.1.0.79 and that worked for me. 

[http://gizmo5.com/pc/download/linux](http://gizmo5.com/pc/download/linux)

Hope this helps,
Eric

---

### Post by mrebanza on 2010-01-30
Google just bought Gizmo5 and took the fkcing source down does anybody still have the original Deb??

---

