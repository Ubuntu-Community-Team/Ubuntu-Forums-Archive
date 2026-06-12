---
title: "DVD playback doesn't work in Jaunty"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SickBeast on 2009-03-14
I tried VLC and Mplayer and I installed the DVD plugins.

VLC comes up with a message saying it can't find the files on the disc.  Mplayer just freezes up.

I have the 180 Nvidia drivers installed.

---

### Post by taavikko on 2009-03-14
Works just dandy here.

Have you installed or compiled the required elements for viewing encrypted
disc's? 

Or maybe just the DVD you're trying to view is b0rked...

---

### Post by rburkartjo on 2009-03-14
yea could be the dvd works just fine here

---

### Post by SoCalChris on 2009-03-15
I'm having the exact same issue. Handbrake begins loading the DVD, and then reports "No valid source". Totem reports "Could not read from resource". I've tried this with approximately 5 DVDs, all look to be in good condition.

edit: Never mind. I just realised that I hadn't added the medibuntu repositories to this machine yet. I added them, and now VLC and Handbrake are working. Totem is still reporting the same error though.

---

### Post by Nullack on 2009-03-15
Just grab the dvd css decryption library from somewhere - for example medibuntu. Personally I dont like adding 3rd party repos so I just download the deb and install it that way.

For mplayer builds, the css decryption library is now statically linked within the mplayer build process so you get it by default within mplayer.

---

### Post by taavikko on 2009-03-15
> **Nullack said:**
> Just grab the dvd css decryption library from somewhere - for example medibuntu. Personally I dont like adding 3rd party repos so I just download the deb and install it that way.


Or one can use the install script that comes with libdvdread4 package.

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```
Note: requires build-essential pgk to build.

---

### Post by Nullack on 2009-03-15
True mate, though I prefer to use the distros package management system so it can be managed better

---

### Post by taavikko on 2009-03-15
> **Nullack said:**
> True mate, though I prefer to use the distros package management system so it can be managed better

Hmm, while using that install-script, it is installed locally, so synaptic detects it. And is removable via apt.

Probably should take a look to that code, to see what it does...

Apparently it wget's it from medibuntu and installs it via dpkg -i

---

### Post by Nullack on 2009-03-15
Nice, Ill look at it

---

