---
title: "Skype 2.1 Beta released -- anyone try it in Karmic?"
date: 2009-08-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by PGScooter on 2009-08-28
Hi,

You can download the deb here:
[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Here is a thread on the general topic:
[http://ubuntuforums.org/showthread.php?t=1251381](http://ubuntuforums.org/showthread.php?t=1251381)

But I am curious if anyone has liked it better/worse with Karmic.

---

### Post by rajeev1204 on 2009-08-28
Brilliant.

A 64 bit version too this time.

---

### Post by Martje_001 on 2009-08-28
And Pulseaudio, just great :-).

---

### Post by Giwex on 2009-08-28
Not working for me: no audio at all :(

---

### Post by rajeev1204 on 2009-08-28
> **Giwex said:**
> Not working for me: no audio at all :(

Hold on,Iam still installing :D

---

### Post by rajeev1204 on 2009-08-28
Green video for now ,i guess have to wait for medibuntu package or somehow make it use v4l1.

---

### Post by rajeev1204 on 2009-08-28
Green video for now ,i guess have to wait for medibuntu package or somehow make it use v4

---

### Post by Giwex on 2009-08-28
Webcam perfect for me but no audio.
I can have the jingle when connecting, then, when the line is connected, no sound. Afterwards no sound at all and even closing Skype doesn't work, it is necessary to kill it

---

### Post by Dawnrazor on 2009-08-28
Does not work here on Karmic 64bit

```
ALSA lib ../../src/conf.c:2700:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib ../../../src/control/control.c:902:(snd_ctl_open_noupdate) Invalid CTL hw:0
Aborted (core dumped)

```

---

### Post by gradinaruvasile on 2009-08-28
> **rajeev1204 said:**
> Green video for now ,i guess have to wait for medibuntu package or somehow make it use v4

for the video problems go here:

[http://forum.skype.com/index.php?showtopic=411441&st=0&gopid=1886611&#entry1886611]("http://forum.skype.com/index.php?showtopic=411441&st=0&gopid=1886611&#entry1886611")

I tried in karmic but pulseaudio keeps crashing (but thats a general phenomenon), i couldnt make it work.
Tried in Jaunty with ALSA, works. 

The video isnt working for my cam out of the box, i used the

```
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
```

command. That way worked.

My webcam is using the gspca driver:

```
0ac8:305b Z-Star Microelectronics Corp. ZC0305 WebCam
```

---

### Post by rewz on 2009-08-28
> **rajeev1204 said:**
> Green video for now ,i guess have to wait for medibuntu package or somehow make it use v4l1.

Same here green video..

---

### Post by rajeev1204 on 2009-08-28
> **rewz said:**
> Same here green video..

That green video problem is nothing new,existed in jaunty too with the change  to video4 linux2.

Ill be taking a look at a previous post someone has given a linke to fix it.

But first,i have to remove pulseaudio because all i hear is static now.

So skype with pulseaudio is useless for me as of now :)

---

### Post by jbernardo on 2009-08-28
Working here on the aspire one using kubuntu-netbook karmic lpia. The only problem was choosing the input sound driver, and playing with the mixer maximizing the capture channel to get decent sound from the mike. And it didn't force me to use pulseaudio, uses alsa without problems.

---

### Post by gradinaruvasile on 2009-08-28
> **rajeev1204 said:**
> That green video problem is nothing new,existed in jaunty too with the change  to video4 linux2.

Ill be taking a look at a previous post someone has given a linke to fix it.

But first,i have to remove pulseaudio because all i hear is static now.

So skype with pulseaudio is useless for me as of now :)

Look at my above post for the answer for video... I had the same problem and it is solved. 

But pulseaudio + karmic is a no-go...

---

### Post by rajeev1204 on 2009-08-28
> **gradinaruvasile said:**
> Look at my above post for the answer for video... I had the same problem and it is solved. 

But pulseaudio + karmic is a no-go...

Yes i was talking about your post there.Thanks for the link.Ill try that one.

But unfortunately,my pulseaudio is dead as of now .Here is bug in case you like to read.

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420597](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/420597)

---

### Post by PGScooter on 2009-08-29
seems like its hit or miss for a lot of people. I wonder why there are so many different experiences. I guess because skype depends on hardware (mic and camera) ? It seems weird to me that audio and video can work perfectly in a different app but not in skype.

---

### Post by rajeev1204 on 2009-08-29
> **gradinaruvasile said:**
> Look at my above post for the answer for video... I had the same problem and it is solved. 

But pulseaudio + karmic is a no-go...

Hi
I get this message

[HTML]LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from LD_PRELOAD cannot be preloaded: ignored.
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
[/HTML]

This fix wont work for 64 bit.Ill have to google a bit more.

---

### Post by portis on 2009-08-29
On 64bit system, you should use
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
instead of /usr/lib/libv4l/v4l1compat.so

---

### Post by rajeev1204 on 2009-08-29
> **portis said:**
> On 64bit system, you should use
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
instead of /usr/lib/libv4l/v4l1compat.so

Hey thanks a million.

That worked.

---

### Post by godhika on 2009-09-09
I found skype is working now perfectly after the latest pulseaudio update today- at least for me (64 bit btw)=D>

---

### Post by cowanh00 on 2009-09-09
> **portis said:**
> On 64bit system, you should use
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
instead of /usr/lib/libv4l/v4l1compat.so

How do you run this from the Skype icon? I can only get it to run from the command line...

---

### Post by papangul on 2009-09-09
Actually, the real 'skype' is renamed 'skype.real' and this 'skype.real' is linked from the user created 'skype' file.

In my 32 bit karmic installation I found this tweaking already in effect, thanks to the package maintainers.

---

### Post by habanany on 2009-10-20
[SIZE=3]**skype 2.1 works perfect in my karmic 32 bits, I can listen and see others through the webcam but unfortunately i cant be heard nor seen. I use logitech notebook deluxe webcam. help please.**[/SIZE]   :mad:

---

### Post by swamytk on 2009-10-20
Here is a simple way to overcome the Green video display and other skype hacks for Ubuntu
[http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/](http://karuppuswamy.com/wordpress/2009/03/01/howto-gear-head-web-cam-093a2620-in-linux/)

---

