---
title: "Is &quot;gnome-web-photo&quot; application broken?"
date: 2009-03-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by moma on 2009-03-03
Hello,

My installation is 64bits Ubuntu 9.04 Alpha5.

Would you like to verify if the GNOME's "gnome-web-photo" application work on Jaunty, especially on 64bits Jaunty. Gnome-web-photo does not work in my installation. It seems to block completly, it does not report any error messages. It just blocks.

I would like to have a second opinion before I file a bug on launchpad.net. 

You can test "gnome-web-photo" with these commands:
[COLOR="SeaGreen"]sudo aptitude install gnome-web-photo[/COLOR]

[COLOR="SeaGreen"]gnome-web-photo --format "png" [http://i1.no](http://i1.no)  result.png[/COLOR]
or
[COLOR="SeaGreen"]gnome-web-photo --mode=photo --format=jpeg [http://i1.no](http://i1.no) result.jpeg[/COLOR]

Gnome-web-photo had earlier some dependency problems ([ref. bug# 325272...]("https://bugs.launchpad.net/ubuntu/+source/gnome-web-photo/+bug/325272")) but I thought those issued were already solved i Jaunty Alpha5.

Thanks in advance.
  Moma

ps. my [gscreendump v0.2]("http://linux1.no/blogg/moma/3632/utrolig-video-om-gscreendump-v02") uses gnome-web-photo a lot. The new amazing Gscreendump v0.2 is almost, almost ready :-)

---

### Post by moma on 2009-03-26
There have been updates on "gnome-web-photo" and related libraries. This is the current situation:

This produces a good result.png.
[COLOR="DarkGreen"]gnome-web-photo --format "png" "http://en.opensuse.org" result.png[/COLOR]
[SIZE="1"]Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)[/SIZE]

However producing JPEG image still fails
[COLOR="DarkGreen"]gnome-web-photo --mode=photo --format=jpeg [http://i1.no](http://i1.no) result.jpeg[/COLOR]
[SIZE="1"]Registering '@mozilla.org/module-loader/python;1' (libpyloader.so)
Registering '@mozilla.org/network/protocol/about;1?what=python' (pyabout.py)
[COLOR="Red"]JPEG parameter struct mismatch: library thinks size is 520, caller expects 504[/COLOR][/SIZE]
---

But [Gscreendump...]("http://code.google.com/p/gscreendump") can live fine with PNG format. Read [this wiki page...]("http://code.google.com/p/gscreendump/wiki/ImageFileFormat")

---

### Post by moma on 2009-04-05
Hello,

I also wonder if "gnome-web-photo" can handle filenames with spaces.
Could anyone double-check this and possibly give me advice how to make it work. 
See: [https://bugs.launchpad.net/ubuntu/+source/gnome-web-photo/+bug/355511](https://bugs.launchpad.net/ubuntu/+source/gnome-web-photo/+bug/355511)

---

### Post by Polygon on 2009-04-05
you are correct, gnome-web-photo had some dependencies problems, but those were solved 

[https://bugs.launchpad.net/shutter/+bug/342408](https://bugs.launchpad.net/shutter/+bug/342408)

i have marked the other bug report you provided in your post as a duplicate and fix released

however, shutter, the program that i originally found this bug with, uses gnome-web-photo and it works fine. And i tried the command that you said was not working, and that worked for me as well (on intrepid, i have to try it in jaunty later)

also, for the spaces question, since the file path is in quotes, you do not need the back slash. i just tried this:

```

gnome-web-photo -t 10 --format "png" --files "/home/mark/Desktop/355511 test.html" result2.png
```


and it worked

---

### Post by moma on 2009-04-10
Hello,
and thank you for your reply.

I ran your command on Ubuntu 8.10 (both 32 bits and 64bits) and it does work right.

$ [COLOR="Green"]touch "$HOME/Desktop/355511 test.html"[/COLOR]
$ [COLOR="Green"]gnome-web-photo -t 10 --format png --files "$HOME/Desktop/355511 test.html" result2.png[/COLOR]

But it absolutely fails on Ubuntu 9.04 beta (64bits).
This is a new installation, all packages updated to the latest version.
The error message is:

Missing arguments!
Usage: gnome-web-photo.real [--mode=photo|thumbnail|print] [...]
Usage: gnome-web-photo.real [-t TIMEOUT] [--force] [--format FORMAT] [-w WIDTH] [--files] URI|FILE OUTFILE [...]

But 9.04 is still in beta so...

---

