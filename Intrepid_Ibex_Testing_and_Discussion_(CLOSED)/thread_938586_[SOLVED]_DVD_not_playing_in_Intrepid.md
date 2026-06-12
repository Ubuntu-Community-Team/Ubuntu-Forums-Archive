---
title: "[SOLVED] DVD not playing in Intrepid"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Zzzach on 2008-10-05
I'm trying to watch X-files season 1 dvd and it won't play. I tried VLC, totem, and mplayer! I have restricted extras installed too. Is there anything I have to do to get DVDs to play on intrepid?

---

### Post by ato on 2008-10-05
[http://ubuntuforums.org/showthread.php?t=937179](http://ubuntuforums.org/showthread.php?t=937179)

---

### Post by Zzzach on 2008-10-05
I installed xine and it started the dvd then it said I needed libdvdcss but it's not in synaptic! I don't know what else to do...

---

### Post by ronacc on 2008-10-05
add the medibuntu repo and libdvdcss will be available .
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by forumache on 2008-10-05
> **ronacc said:**
> add the medibuntu repo and libdvdcss will be available .
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

*DO NOT* add other repositories!

You have everything ready to be installed, on your system.

The dvdread comes with support for decss, to decrypt the DVDs. It is not installed yet, but you need only one command, which comes with dvdread:

sudo /usr/share/doc/libdvdread3/install-css.sh

as simple as that!

---

### Post by Nullack on 2008-10-05
Yeah, Im against adding external repos too.

To be clear : is the decryption script for css not run on install of dvdread / dvdnav??

---

### Post by xreaper on 2008-10-05
hey, try:

sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

then 

sudo /usr/share/doc/libdvdread3/install-css.sh

that should work for you ^^

---

### Post by Robertjm on 2008-10-05
Really? I thought that you needed to install libdvdcss to play COMMERCIAL DVDs in your system and the only way to get that was through Mediabuntu, not to mention the codecs needed to play them.

Robert

> **forumache said:**
> *DO NOT* add other repositories!

You have everything ready to be installed, on your system.

The dvdread comes with support for decss, to decrypt the DVDs. It is not installed yet, but you need only one command, which comes with dvdread:

sudo /usr/share/doc/libdvdread3/install-css.sh

as simple as that!

---

### Post by forumache on 2008-10-05
> **Robertjm said:**
> Really? I thought that you needed to install libdvdcss to play COMMERCIAL DVDs in your system and the only way to get that was through Mediabuntu, not to mention the codecs needed to play them.

Robert,

the codecs are installed automatically when you try to play a DVD (from universe/multiverse). The same when you try to play a MP3. You'll get a dialog box saying "be sure that is legal in your country, etc.", you say yes (not you, because for you being in USA it may be illegal) and that's it, the codecs are downloaded and the MP3 starts playing.

Following this you can play unencrypted DVDs (I think all not region coded).

For decss, the proper way to install it is the one specified in the dvdread library (it comes with support of decss, but in needs to be manually installed by running the script)

---

### Post by forumache on 2008-10-05
> **Nullack said:**
> Yeah, Im against adding external repos too.

To be clear : is the decryption script for css not run on install of dvdread / dvdnav??

No, the decryption script does not run automatically. I guess it should, but it was made that way to avoid installing potentially illegal software.
The user might be from USA, in this case he/she should be warned about the DMCA and stuff. For Europe, it is OK to install it automatically. I think the idea was to give a choice to the user.

---

### Post by Nullack on 2008-10-05
> **xreaper said:**
> hey, try:

sudo apt-get install totem-xine libxine1-ffmpeg libdvdread3

then 

sudo /usr/share/doc/libdvdread3/install-css.sh

that should work for you ^^

I dont recommend running xine if you want other multimedia stuff to work as well - gstreamer generally does a better job as my tests have shown. Hopefully the progress with resindvd will into the short term future bring robust dvd menu support.

---

### Post by Zzzach on 2008-10-08
> **ronacc said:**
> add the medibuntu repo and libdvdcss will be available .
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Thanks! That worked. DVD problem solved! :popcorn:

---

