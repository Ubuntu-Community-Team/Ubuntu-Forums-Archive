---
title: "Phonon problems, no sound after KDE 4.4 upgrade"
date: 2010-02-26
forum: Installation &amp; Upgrades
---

### Post by Flake Remix on 2010-02-26
Hello,

I was a happy user before I upgraded to KDE 4.4 in my Kubuntu 9.10. Basically I added *ppa:kubuntu-ppa/backports* to sources list as it's said here: [http://www.kubuntu.org/news/kde-sc-4.4](http://www.kubuntu.org/news/kde-sc-4.4)

After I refreshed the packages list, there appeared equally big two lists with new packages, normal packages and so named as "blocked", if I remember correctly. Anyway, I selected normal ones and did update.

Now every boot I get this kind of warnings:
[IMG]http://i50.tinypic.com/23vj679.png[/IMG]
[IMG]http://i45.tinypic.com/4ufl12.png[/IMG]
No sound in any application, except in Multimedia settings:
[IMG]http://i47.tinypic.com/2czr77l.png[/IMG]
Here I hear music if I select a device and press Test.

I decided to do another test, I installed Kubuntu 9.10 in VMware and upgraded to KDE 4.4, the same problem:
[IMG]http://i47.tinypic.com/4vlmoo.png[/IMG]
[IMG]http://i50.tinypic.com/2uj5c46.png[/IMG]

Is it possible to fix this? I don't want to reinstall the whole system :(

---

### Post by seeker5528 on 2010-02-26
Did  you try deferring the pulse-audio output and preferring the one you actually one it to use?

If I am taking things correctly by this image
[img]http://i47.tinypic.com/2czr77l.png[/img]

you were in the accessibility category when you did the test and the test worked? If it worked there it should work for the main sound output and the other categories.

If pulseaudio is installed you may want to remove it and any other pulseaudio-* packages might be installed.

Later, Seeker

---

### Post by Flake Remix on 2010-02-26
> **seeker5528 said:**
> Did  you try deferring the pulse-audio output and preferring the one you actually one it to use?

I tried to reorder devices, but it didn't help. The one I actually use is HDA Nvidia Analog, the first one.

> If I am taking things correctly by this image
[img]http://i47.tinypic.com/2czr77l.png[/img]

you were in the accessibility category when you did the test and the test worked? If it worked there it should work for the main sound output and the other categories.

Yes, it works in other categories too.

> If pulseaudio is installed you may want to remove it and any other pulseaudio-* packages might be installed.

I have no pulseaudio installed, at least dpkg doesn't list it:
```
dpkg -l | grep pulse
ii  libpulse-mainloop-glib0              1:0.9.19-0ubuntu4.1                        PulseAudio client libraries (glib support)
ii  libpulse0                            1:0.9.19-0ubuntu4.1                        PulseAudio client libraries
```

Removing libpulse-mainloop-glib0 will remove kubuntu-desktop too - sounds scary, and removing libpulse0 will clean half of the system, 131 packages with size of ~300MB - even worse.

More on that, why does it think that the integrated audio has been removed, that makes no sense. May be try to downgrade Phonon? Though I don't really know how.

---

### Post by seeker5528 on 2010-03-01
> **Flake Remix said:**
> Removing libpulse-mainloop-glib0 will remove kubuntu-desktop too - sounds scary, and removing libpulse0 will clean half of the system, 131 packages with size of ~300MB - even worse.

Libpulse-mainloop-glib0 and libpulse0 are just libraries packages, so not a big deal, and as you found out they are depended on by a lot of things, or at least some key things the affect a lot of other packages.

Looking around my system for phonon stuff.... the next likely suspect seems to me like it would be '~/.kde/share/config/phonondevicesrc', and the next thing to try would be to open a terminal window and type:

```
cd ~/.kde/share/config/
mv phonondevicesrc phonondevicesrc.old
```

or if you prefer you can browse there in the file manager and rename it, in Dolphin you have to go to the 'View' menu and check the 'View Hidden Files' box to see files and directories that start with a dot.

After you have renamed the file log out and log in a gain and a new copy of the file should be created automatically. 

Later, Seeker

---

### Post by isaacahloe on 2010-03-03
this worked for me. I love fixing things by resetting the config files.

---

### Post by DroBuddy on 2010-03-18
> **seeker5528 said:**
> 

```
cd ~/.kde/share/config/
mv phonondevicesrc phonondevicesrc.old
```

After you have renamed the file log out and log in a gain and a new copy of the file should be created automatically. 

Later, Seeker

I upgraded from Kubuntu Jaunty to Karmic and was getting this error; I did a fresh install of Karmic and still had this problem. After doing Seeker's suggestion, the problem is solved.

Thanks, Seeker. This had been bothering me for like two weeks. lol. I really do appreciate it. Peace.

---

### Post by coderasm on 2011-04-04
Thank you very much. This solved my problem in Maverick 10.10.

---

### Post by piatros on 2011-07-03
I have had ubuntu 10.04 installed in my computer and after installing KDE 4.4, it pops up a windows notice saying; the sound for intel HD generic is not working. I'd try to apply the sound serching for the ALSA driver chip list to find the one my machine use to install it. Once I enter the page I didn't found the module for my machine which is 82801I (ICH9Family) HD Audio Controller. May anyone help me with this issue? Thanx from Piatros!!!

---

