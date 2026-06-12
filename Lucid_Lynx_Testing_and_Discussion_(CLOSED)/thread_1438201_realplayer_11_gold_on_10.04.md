---
title: "realplayer 11 gold on 10.04"
date: 2010-03-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by fritzman on 2010-03-24
I still use realplayer.  I know....there are lots of others I could use, but, I like the way I have it set up.  Anyway, I do the standard;
$ cd folder containing RealPlayer11GOLD.bin
$ chmod a+x RealPlayer11GOLD.bin
$ sudo ./RealPlayer11GOLD.bin
$ file not found

But, I've been using it on 9.04 and 9.10.  I downloaded a new one, and tried it again with the same results.
Any ideas?

---

### Post by sxmaxchine on 2010-03-24
i think realplayer is linked to a lot of dll files and wine isnt able to work around them all anyway i like realplayer to it a great program.

---

### Post by wojox on 2010-03-24
$ cd folder containing RealPlayer11GOLD.bin
$ ls
$ sudo chmod +x RealPlayer11GOLD.bin
$ ./RealPlayer11GOLD.bin

---

### Post by fritzman on 2010-03-24
> **wojox said:**
> $ cd folder containing RealPlayer11GOLD.bin
$ ls
$ sudo chmod +x RealPlayer11GOLD.bin
$ ./RealPlayer11GOLD.bin

Been there, done that, twice.  Same results.

---

### Post by fritzman on 2010-03-24
> **sxmaxchine said:**
> i think realplayer is linked to a lot of dll files and wine isnt able to work around them all anyway i like realplayer to it a great program.

Not running realplayer on wine.  Using the linux version, RealPlayer11GOLD.bin

---

### Post by wojox on 2010-03-25
I didn't realize you where on Lucid. Can you install any other .bin files? GoogleEarth? 

You may want to look into or file a bug report on not being able to install .bin files.

---

### Post by Mark Phelps on 2010-03-25
Please post your Lucid-related issues to the proper forum: Development & Programming, Lucid Lynx Testing.

Am requesting the Mods to move this thread accordingly.

Please look for further responses there.

---

### Post by Ibidem on 2010-03-25
May I ask why you're not trying [this installer]("http://forms.real.com/real/player/download.html?f=unix/RealPlayer11GOLD.deb")?
A .deb is usually preferable.  
(Note that it is ~1MB larger, 8.2 mb, and has tons of odd dependencies)
The .bin works for me, though.

(Of course, my system is still stuck somewhere just past alpha2, but I don't *think* that should make a difference)
Ibidem

---

### Post by fritzman on 2010-03-28
The .deb download from RealPlayer site is broken.  It looks like it might actually be launching binary code, and it is visible on my screen.
As regards Lucid, I've decided that I haven't the time to tinker with a pre-released version at this time.  So, I caused the partition holding Lucid to become free electrons, floating about the air.  
My next toy was to download and install Windows 7 using VirtualBox.  Looks pretty good, so far.  But my experience is that Windows of any ilk runs good in a virtual environment.  It really chokes, though, on real hardware.  So my next adventure will be to install Windows 7 on the partition just vacated by Lucid to see how it does running native.  
The neat thing about the win7.iso install, though, is that it does NOT demand the license string in order to install.  It quietly lets you try it for 30 days, at which time it becomes unbootable.  So, if you're going to spend the money for a license, you need to do it before the end of the 29th day.
Lucid looks like I'll like it, but, as I said, I really don't have the time to tinker with a pre-release version.  So, I'll just wait for the actual release in 6 or 8 weeks.
Thanks, everyone for your responses.  They were very much appreciated.
owa

---

