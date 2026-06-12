---
title: "Can you use fglrx in karmic?"
date: 2009-05-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Duskao on 2009-05-25
Well, can you? hehehe. Got a Radeon 4850.

---

### Post by Naddiseo on 2009-05-26
> **Duskao said:**
> Well, can you? hehehe. Got a Radeon 4850.

I haven't been able to get it working, but the open source ones are good enough for me. I seem to remember reading something about it not working with karmic's kernels.

---

### Post by super.rad on 2009-05-26
No fglrx doesn't support the .30 kernel, there may be a patch for it somewhere but don't think you'll have much luck without one

---

### Post by Ubuntiac on 2009-07-25
Well, I have a 4850, too. Restricted driver manager told me there was a driver available. I chose it, activated and... it hosed my X. No amount of xorg.conf tweaking got it back and I'm re-installing as I type this.

I'd wait until you hear the kernel is supported by fglrx. :$

---

### Post by markbuntu on 2009-07-25
Supposedly 9.8 will have support for the 2.6.30 kernel. There are some patches around from some gentoo folks. There is directions for them in here somewhere

[http://ubuntuforums.org/showthread.php?t=1164815](http://ubuntuforums.org/showthread.php?t=1164815)

---

### Post by taavikko on 2009-07-25
> **Ubuntiac said:**
> it hosed my X. No amount of xorg.conf tweaking got it back and I'm re-installing as I type this.


How about in recovery mode:
```
aptitude purge xorg-driver-fglrx && dpkg-reconfigure -phigh xserver-xorg && exit
```

And resume normal boot ;) for the next time this issue rises with fglrx-blob.

---

### Post by deadspider187 on 2009-07-25
They just released 9.7, maybe that will work?  I'm using Karmic right now, and the choice is between radeon w/decent video playback but w/o 3d, and radeonhd w/o any acceleration.

---

### Post by taavikko on 2009-07-25
> **deadspider187 said:**
> They just released 9.7, maybe that will work?  I'm using Karmic right now, and the choice is between radeon w/decent video playback but w/o 3d, and radeonhd w/o any acceleration.

9.7 won't work. 9.8 will supposedly have fix for this.
you can get somekind of an eyecandy using metacity with compositing.
Both radeon/radeonhd

---

### Post by Ubuntiac on 2009-07-26
Strangely enough, running KDE 4.3 (RC3) and ATI (Radeon?) I can actually use 3d in Blender, but desktop effects still fail. (The automatic test won't pass it for compositing).

*sigh*

I miss my wobbly windows!

---

### Post by deadspider187 on 2009-07-26
> **taavikko said:**
> 9.7 won't work. 9.8 will supposedly have fix for this.
you can get somekind of an eyecandy using metacity with compositing.
Both radeon/radeonhd


Do you have any links to get compositing working?  I can't get this to work with any configurations I've tried.

---

### Post by Ubuntiac on 2009-07-27
> **taavikko said:**
> 9.7 won't work. 9.8 will supposedly have fix for this.

All the comments I'm seeing seem to refer to .30 version of the Kernel, where my Karmic seems to be on .31....

---

### Post by vicho on 2009-07-29
Hi,
french user so bad english...
xorg.conf does not exit in karmic, so how can I know the used driver?
I installed radeonhd but I don't know if i use it.
Thank you in advance for your help

Config :
Intel Core2Duo E8400 ; CM : Asus Maximus Formula X38
CG : HD4890 ; Ram : 4Go
OS : Dual Boot Ubuntu; WinXP

---

### Post by uBeer on 2009-07-29
> **deadspider187 said:**
> Do you have any links to get compositing working?  I can't get this to work with any configurations I've tried.

For metacity compositing:

GUI:
start up gconf-editor with Alt-F2 or from terminal.
Change /apps/metacity/general/compositing_manager from false to true.
Now you get shadows and composited windows and the ability to use docky.

Commandline:
```
gconftool --type bool --set /apps/metacity/general/compositing_manager true
```

---

### Post by ghostbyte on 2009-07-29
I was using fglrx in Alpha 2 and it worked fine. The driver was the only reason I installed 9.10. The next day Alpha 3 was out and it no longer worked. I really hope it works before release.

---

### Post by Ubuntiac on 2009-07-30
They usually release the new version, even if only a working beta, just before to just after launch.

---

### Post by zFrenchman on 2009-10-16
i have a radeon 4850 running on karmic and the fglrx drivers run fine for me, there is just a small problem with vertical sync, but overall im getting glx gears of 18000 frames per second and running compiz great as well

---

### Post by Ubuntiac on 2009-10-17
Yup. It's working good for me, too on an ATI HD4850. :)

---

### Post by vicho on 2009-10-19
Hi all,
thank you for your answers.
I think I had a bad couple kernel/driver.
Now it works fine.
Good night (or morning, day...) for french people !

---

### Post by NCLI on 2009-10-19
Please mark as solved. :)

---

### Post by vicho on 2009-10-19
Duskao is the god of the topic...
I'm just a slave!!!

---

