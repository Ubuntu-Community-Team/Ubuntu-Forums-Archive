---
title: "Can't watch movie/video files"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by Rhemat on 2005-05-22
I try to use totem, but it gives this message:

"The Application "totem" has quit unexpectedly.

You can inform the developers of what happened to help them fix it.  Or you can restart the application right now."

I've tried installing MPlayer, but it always requests a file/directory called libpng and libpng-dev, and I can't find such files.

Is there a way to fix totem or Mplayer, or should I try to find a better player?

Thank you for your help.

-Brad

---

### Post by 23meg on 2005-05-22
you should be able to find the missing libraries if you [enable extra repositories.](http://www.ubuntuguide.org/#extrarepositories) . 

also try [installing the multimedia codecs](http://www.ubuntuguide.org/#codecs) if you haven't. and install totem-xine as well if all goes wrong.

---

### Post by Sam on 2005-05-22
Did you [install the multimedia codecs](http://ubuntuguide.org/#codecs) ?
For the missing lib, try:
```
$ sudo apt-get install libpng12-0 libpng12-dev
```

If both doesn't do anything, open totem from a terminal and paste the output here.

---

### Post by Rhemat on 2005-05-23
Alright, I have the font-arial-iso-8859-1 folder, a blue skin folder, libavcodec folder, and the libpng-1.2.8 folder all in my mplayer folder.  I think I had them configure with:

 ./configure --with-datadir=[corresponding folder directory here].

One problem I think I may be having is that it wants me to put the files in /usr/local/share/ etc. and even though I have root priv. in terminal, I can't do it in the gui.  Does the earlier string force it to look in the corresponding directory, or is there something else I need to do.

Also, possibly a dumb question, but will MPlayer work on Ubuntu 4.10?

Thanks again,

-Brad

---

### Post by Rhemat on 2005-05-23
I almost forgot, I appearantly don't have the file gmplayer.  Mplayer seems to work it'll say that it is playing a file in terminal, then saying "file end/exiting or something like that, but doesn't visuallize anything.
  Sorry I have to keep asking all of you questions, but I'm not used to downloading piece by piece of a program.

Thanks again.

-Brad

---

### Post by Rhemat on 2005-05-29
Hello again,
  Well, after a while of trying to get everything configured and searching for things that I thought it needed, I messed up my computer some how and had to reinstall Ubuntu (I somehow made it to where after logging in it would open terminal but block everything else (?)).  Oddly enough, though, Ubuntu now finds my sound card (more like built in chip), so that's a plus.
  Anyway, I'm going to try to use the official guide, download the source/core, a font, a skin, but I can't find a file that it needs to configure the GUI.  It is a GTK devel package, and I've tried to use apt-get to download gtk, gtk-dev, gtk-devel, but nothing works.  Also, if needed, how can I use root priveleges in the gui so they go in the proper folders, or point to where they are when in terminal?

Thanks again

-Brad

---

