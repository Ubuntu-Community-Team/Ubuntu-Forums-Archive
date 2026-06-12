---
title: "Updating from 10.04"
date: 2016-01-11
forum: Installation &amp; Upgrades
---

### Post by random turnip on 2016-01-11
While moving house I discovered my old laptop which hasn't been booted for 4-5 years and to my surprise after a bit of a charge it worked fine (apart for some artifacting, but that's going to be another thread...)

However it's on 10.04, which is no longer supported and so the update center doesn't pick anything up. Is there anything I can do to get around this or would I need a fresh install?  I'd rather avoid that as I'm just looking for a quick fix for now, but not the end of the world if I have to.

---

### Post by yancek on 2016-01-11
I think you would first need to upgrade to 12.04 and then to 14.04.  See the Ubuntu site below.  Much easier to install the current LTS, 14.04 and will certainly take less time. 

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_10.04_LTS_to_Ubuntu_12.04_LTS)

---

### Post by Bucky Ball on 2016-01-11
A clean install would be the quickest fix. Trying to upgrade an EOL is a trick in itself, then you need to do the actual upgrade, which takes about two or more hours, depending on your ethernet speed, and test the upgraded OS, then do it all again to get to 14.04 LTS. A lot has changed since 10.04 and I can't see anything good coming from this, unless you consider a headache, frustration, and many of waiting and problem solving good. 

Also, what hardware do you have? The latest Ubuntu may not work well on it anyway. The newer release is bulkier than 10.04 and more resource hungry. 

If you've backed it up or have nothing worth saving on there in the first place, a clean install will take about an hour, possibly less. How long for configuring to your liking will vary, of course. 

Good luck.

---

### Post by random turnip on 2016-01-11
Thanks guys, will just do a fresh install then, not likely to have much on there that's needed.

I was going to ask about recommended specs actually,  can't seem to find them on the website, could anyone point me in the right direction?
If it's not looking good might try Xubuntu or maybe an entirely different distro.

---

### Post by Bucky Ball on 2016-01-11
How much RAM have you got? Xubuntu is definitely worth a go. It's (almost) what I use. I don't like Unity.

---

### Post by yancek on 2016-01-11
The minimum hardware requirements are at the Ubuntu page below.  There are links to Lubuntu and Xubuntu as well.  These are basically the absolute minimums.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by random turnip on 2016-01-11
I have 2GB RAM and a 2.16 GHz dual core CPU ([HP Pavillion dv9000]("http://www.cnet.com/uk/products/hp-pavilion-dv9000/specs/")).  Which seems like it should be more than good enough for newer versions of Ubuntu anyway?

---

### Post by grahammechanical on 2016-01-11
There is a key component that you do not mention and that is the graphic card. What is it? Can it do accelerated 3D rendering in hardware? How much of its own memory does it have?

I doubt if this command will work in 10.04 but from a live session of 12.04 upwards it should work.

```
/usr/lib/nux/unity_support_test -p
```

You need to see something like this

> OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GT 220/PCIe/SSE2
OpenGL version string:  3.3.0 NVIDIA 340.96

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes

There is another factor that you should be aware of. The present Ubuntu user interface (Unity 3D) looks nothing like the UI in 10.04. The change began, I think, with 11.04. So, if you are not aware of the present look of Ubuntu, do not expect it to look like 10.04. 

Xubuntu & Lubuntu & Ubuntu Mate each retain something of the old style.

Regards

---

### Post by Bucky Ball on 2016-01-11
Should run okay, with the points raised by grahammechanical as caveats. Graphics card and your taste in interface. Ubuntu Gnome is also very similar to 10.04 LTS. Unity is nothing like it.

What you might like to try is creating install media, boot from it, choose 'Try Ubuntu' from the options and take 14.04 for a test drive. See what you think of Unity and see how 14.04 cooperates with your hardware.

---

### Post by random turnip on 2016-01-12
> **grahammechanical said:**
> There is a key component that you do not mention and that is the graphic card. What is it? Can it do accelerated 3D rendering in hardware? How much of its own memory does it have?

I doubt if this command will work in 10.04 but from a live session of 12.04 upwards it should work.

```
/usr/lib/nux/unity_support_test -p
```

You need to see something like this



There is another factor that you should be aware of. The present Ubuntu user interface (Unity 3D) looks nothing like the UI in 10.04. The change began, I think, with 11.04. So, if you are not aware of the present look of Ubuntu, do not expect it to look like 10.04. 

Xubuntu & Lubuntu & Ubuntu Mate each retain something of the old style.

Regards

Thanks, not too sure what the GPU is capable of, will check this before I waste a CD.

> **Bucky Ball said:**
> Should run okay, with the points raised by grahammechanical as caveats. Graphics card and your taste in interface. Ubuntu Gnome is also very similar to 10.04 LTS. Unity is nothing like it.

What you might like to try is creating install media, boot from it, choose 'Try Ubuntu' from the options and take 14.04 for a test drive. See what you think of Unity and see how 14.04 cooperates with your hardware.
Good to know this feature is still there, will try it before I install.  Assume it still runs rather slow from the CD though.

---

### Post by Bucky Ball on 2016-01-12
Ubuntu no longer runs from a CD at all. Won't fit. DVD or USB.

---

### Post by random turnip on 2016-01-14
Ah bum.  Will have to go and get some, or maybe if I'm lucky a Linux magazine will have one included or something, would probably be cheaper than a pack of DVDs just to use 1.  Take it you could still make a live CD for any Ubuntu flavour?

The command to see if Unity would run doesn't work on 10.04.

---

### Post by Bucky Ball on 2016-01-14
Like I said, you can also use USB. 

UNetbootin:
[www.unetbootin.sourceforge.net](www.unetbootin.sourceforge.net)

Universal USB Installer:
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

---

