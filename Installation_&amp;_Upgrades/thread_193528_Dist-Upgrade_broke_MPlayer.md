---
title: "Dist-Upgrade broke MPlayer?"
date: 2006-06-10
forum: Installation &amp; Upgrades
---

### Post by Timokl on 2006-06-10
Hi folks,

last week I upgraded from Breezy to Dapper. Generally, that transition was quite smooth, just some Multimedia apps make problems.

On Breezy, I used MPlayer without problems. But after the upgrade, Mplayer won't start any more. When I open it through the Gnome menu, I see the hard drive's LED blink, then a little window or dialog pops up, and closes instantly. It's visible just for a tiny fraction of a second. And then nothing ... 

I tried re-installing it several times. There does not seem to be a problem with the dependency.

Here's a list of my installed Mplayer packages:

```
timo@ubuntu:~$ dpkg -l 'mplayer*'
Gewünscht=Unbekannt/Installieren/R=Entfernen/P=Säubern/Halten
| Status=Nicht/Installiert/Config/U=Entpackt/Fehlgeschl. Konf./Halb install.
|/ Fehler?=(keiner)/Halten/R=Neuinst. notw/X=beides (Status, Fehler: GROß=schlecht)
||/ Name           Version        Beschreibung
+++-==============-==============-============================================
ii  mplayer        0.99+1.0pre7tr The Ultimate Movie Player For Linux
un  mplayer-386    <keine>        (keine Beschreibung vorhanden)
un  mplayer-586    <keine>        (keine Beschreibung vorhanden)
un  mplayer-686    <keine>        (keine Beschreibung vorhanden)
un  mplayer-amd64  <keine>        (keine Beschreibung vorhanden)
un  mplayer-custom <keine>        (keine Beschreibung vorhanden)
ii  mplayer-doc    0.99+1.0pre7tr The Ultimate Movie Player For Linux (Documen
ii  mplayer-fonts  3.5-2          Fonts for mplayer
un  mplayer-g4     <keine>        (keine Beschreibung vorhanden)
pn  mplayer-k6     <keine>        (keine Beschreibung vorhanden)
ii  mplayer-k7     0.99+1.0pre7tr The Ultimate Movie Player For Linux (dummy p
un  mplayer-nogui  <keine>        (keine Beschreibung vorhanden)
un  mplayer-powerp <keine>        (keine Beschreibung vorhanden)
ii  mplayer-skins  2-6            Skins for the Ubuntu mplayer Package
un  mplayerplug-in <keine>        (keine Beschreibung vorhanden)

```

I use Dapper 32 Bits with an AMD Turion64 cpu, if that should make any difference.

Any ideas?

Bye,
Timo

---

### Post by angkor on 2006-06-10
What does it say when you start mplayer from the terminal?

```
mplayer {path/to/video/file}
```


btw, congratulations to your king. :)

---

### Post by Timokl on 2006-06-10
> **angkor]What does it say when you start mplayer from the terminal?

```
mplayer {path/to/video/file}
```[/QUOTE]

That's the power of the command line. Then I get a normal playback. I tried it with an .ogg and a Real-Media file.

```
timo@ubuntu:~$ mplayer ./Deep\ Purple/Gemini\ Suite/01-deep\ purple-first\ movement\:\ guitar\,\ voice.ogg
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer said:**
>  stream 0: audio (Vorbis), -aid 0
Ogg file format detected.
Clip info:
 Name: First Movement: Guitar, Voice
 Artist: Deep Purple
 Track: 1
 Album: Gemini Suite
 Genre: Classic Rock
==========================================================================
Opening audio decoder: [libvorbis] Ogg/Vorbis audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 160.0 kbit/11.34% (ratio: 20000->176400)
Selected audio codec: [vorbis] afm: libvorbis (OggVorbis Audio Decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Video: no video
Starting playback...
A:  34.2 (34.1) of 1042.9 (17:22.8)  2.3%
alsa-uninit: pcm closed

Exiting... (End of file)
timo@ubuntu:~$ mplayer ./Wahlwerbespots\ 2006/spd-2005-kugel.rm
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer; Athlon 64 X2 Toledo; Turion Newark,Lancaster (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.


91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing ./Wahlwerbespots 2006/spd-2005-kugel.rm.
REAL file format detected.
Stream description: Video Stream
Stream mimetype: video/x-pn-realvideo
Stream description: Audio Stream
Stream mimetype: audio/x-pn-realaudio
VIDEO:  [RV40]  320x240  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, s16le, 44.1 kbit/3.12% (ratio: 5512->176400)
Selected audio codec: [ffcook] afm: ffmpeg (FFmpeg COOK audio decoder)
==========================================================================
==========================================================================
Opening video decoder: [realvid] RealVideo decoder
opening shared obj '/usr/lib/win32/drvc.so'
Selected video codec: [rv3040] vfm: realvid (Linux RealPlayer 10 RV30/40 decoder)
==========================================================================
Building audio filter chain for 44100Hz/2ch/s16le -> 0Hz/0ch/??...
alsa-init: 1 soundcard found, using: default
alsa: 44100 Hz/2 channels/4 bpf/60208 bytes buffer/Signed 16 bit Little Endian
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Building audio filter chain for 44100Hz/2ch/s16le -> 44100Hz/2ch/s16le...
Starting playback...
VDec: vo config request - 320 x 240 (preferred colorspace: Planar I420)
VDec: using Planar I420 as output csp (no 0)
Movie-Aspect is 1.33:1 - prescaling to correct movie aspect.
VO: [xv] 320x240 => 320x240 Planar I420
alsa-space: xrun of at least 0.192 msecs. resetting stream?,?% 0 0
No bind found for key 'MOUSE_BTN2'                         .0% 6 0
alsa-space: xrun of at least 0.105 msecs. resetting stream2.0% 6 0
A:  29.7 V:  30.0 A-V: -0.239 ct:  0.009 751/751 12%  0%  2.0% 6 0
alsa-uninit: pcm closed

Exiting... (End of file)


```


[QUOTE]btw, congratulations to your king. :)

Well, I am not Thai, but anyway: &#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3588;&#3619;&#3633;&#3610;

Bye,
Timo

---

### Post by angkor on 2006-06-10
> **Timokl]It says the following:

```
timo@ubuntu:~$ mplayer

```[/quote]

You need to specify a video file when starting mplayer from the terminal.

Copy a video to your home, open up a terminal and type:

```
mplayer {name_of_your_video}
```

and replace name_of_your_video with the file you copied.

[quote=Timokl[/quote]
Well, I am not Thai, but anyway: &#3586 said:**
> 

Ah, okay. Well still happy celebrations, I heard there were 1M people celebrating in the streets of bangkok.

[quote]&#3586;&#3629;&#3610;&#3588;&#3640;&#3603;&#3588;&#3619;&#3633;&#3610;

what does that say? kap-kun-kap? :)

---

### Post by Timokl on 2006-06-10
[QUOTE=angkor]You need to specify a video file when starting mplayer from the terminal.[/QUOTE]

I figured that out, right **after** clicking on Send. :rolleyes: 

I updated my original post, but you were quicker. 

From the command line everything seems to work. Looks like a problem with the GUI.

> Ah, okay. Well still happy celebrations, I heard there were 1M people celebrating in the streets of bangkok.

I only saw it on TV, quite overwhelming. On the way to work, I saw everybody in the yellow shorts that say "We love the king".

> what does that say? kap-kun-kap? :)

Right. Or: Thank you for the English speaking world. :-)

Bye,
Timo

---

### Post by angkor on 2006-06-10
[QUOTE=Timokl]I updated my original post, but you were quicker. 
[/QUOTE]

That's strange. Mplayer is meant to be started in the terminal, it's normal that clicking mplayer in the gui doesn't do anything. It should load **g**mplayer (mplayer with gui) though.

What happens if you double-click a video file, does it open in mplayer?

---

### Post by angkor on 2006-06-10
I just thought of something.

Open up the Alacarte Menu editor (Applications -> Accessories) and go to Sound & Video.

Right click mplayer and select properties.

In the command box it should say: 'gmplayer'. If it doesn't change it and try the menu item again.

---

### Post by Timokl on 2006-06-10
[QUOTE=angkor]I just thought of something.

Open up the Alacarte Menu editor (Applications -> Accessories) and go to Sound & Video.

Right click mplayer and select properties.

In the command box it should say: 'gmplayer'. If it doesn't change it and try the menu item again.[/QUOTE]

Just checked. The menu editor says 'gmplayer' indeed.

I tried then to run a video through the command line with the command **g**mplayer. This did not work. It opens a window and closes it instantly.

In the terminal I read the following:

```
timo@ubuntu:~$ gmplayer ./Wahlwerbespots\ 2006/spd-2005-kugel.rm
MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Advanced Micro Devices Athlon 64 Clawhammer; Athlon 64 X2 Toledo; Turion Newark,Lancaster (Family: 15, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.



91 audio & 204 video codecs
/usr/share/fonts/truetype/msttcorefonts/Arial.ttf doesn't look like a font description, ignoring.
Cannot load font: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
[skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.
Skin not found (default).

```

---

### Post by angkor on 2006-06-10
[quote=Timokl][skin] file ( /usr/share/mplayer/Skin/default/skin ) not found.[/quote]

I think this is your problem. Install the skins package and try again.

```
sudo apt-get install mplayer-skins
```

---

### Post by dnccnd on 2006-06-10
[QUOTE=angkor]What does it say when you start mplayer from the terminal?

```
mplayer {path/to/video/file}
```
[/QUOTE]

I am having exactly the same problem!  When I type the quoted command line I get this:

MPlayer 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8 (C) 2000-2006 MPlayer Team
CPU: Intel Celeron 2/Pentium III Tualatin (Family: 6, Stepping: 1)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 0
Compiled with runtime CPU detection.

91 audio & 204 video codecs
Linux RTC init error in ioctl (rtc_irqp_set 1024): Permission denied
Try adding "echo 1024 > /proc/sys/dev/rtc/max-user-freq" to your system startup scripts.
Opening joystick device /dev/input/js0
Can't open joystick device /dev/input/js0: No such file or directory
Can't init input joystick
Setting up LIRC support...
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support.
You will not be able to use your remote control.
Playing {path/to/video/file}.
File not found: '{path/to/video/file}'
Failed to open {path/to/video/file}

Exiting... (End of file)


The wierd thing is that I can't open Totem Movie Player either, but if I open a movie file Totem works, while Mplayer doesn't.

nother wierd thing is that in Add/Remove Application, Totem is not given as installed, while Mplayer is checked as installed. :confused: 

I tried with the skins, but it says I have already the newest skins.

In Alacarte Mplayer is already gmplayer.

Thanks for any help you can provide...

---

### Post by angkor on 2006-06-10
[QUOTE=dnccnd]
I tried with the skins, but it says I have already the newest skins.
[/QUOTE]

How strange, what happens if you manually install a skin. Download one from here and install in the specified directory (/usr/share/mplayer/Skin/default/).

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Also, what mplayer package does Synaptic say you have installed?

---

### Post by dnccnd on 2006-06-10
[QUOTE=angkor]How strange, what happens if you manually install a skin. Download one from here and install in the specified directory (/usr/share/mplayer/Skin/default/).

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

Also, what mplayer package does Synaptic say you have installed?[/QUOTE]

Unfortunately, the url you provided doesn't work.

I can see that these are the Mplayer componets installed on my system:

mozilla-mplayer 3.17-lubuntu1
mplayer 2:0.99+1.0pre7try2
mplayer-586 2:0.99+1.0pre7try2
mplayer fonts 3.5-2
mplayer skins 2-6

Thankyou!

---

### Post by Timokl on 2006-06-10
[QUOTE=dnccnd]Unfortunately, the url you provided doesn't work.

I can see that these are the Mplayer componets installed on my system:

mozilla-mplayer 3.17-lubuntu1
mplayer 2:0.99+1.0pre7try2
mplayer-586 2:0.99+1.0pre7try2
mplayer fonts 3.5-2
mplayer skins 2-6

Thankyou![/QUOTE]

The same goes for me. It's definitely not the Skin problem, as the package is installed already.

```
timo@ubuntu:~$ sudo apt-get install mplayer-skins
Password:
Paketlisten werden gelesen... Fertig
Abhängigkeitsbaum wird aufgebaut... Fertig
mplayer-skins ist schon die neueste Version.
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.

```

(Sorry for posting in German, but I use the de-locale. :-) It basically says, that the newest version of mplayer-skins is installed.

---

### Post by angkor on 2006-06-11
[QUOTE=dnccnd]Unfortunately, the url you provided doesn't work.
[/QUOTE]

Hmm, they've changed the url, this one should work for the skins.

[http://www.mplayerhq.hu/homepage/design7/dload.html](http://www.mplayerhq.hu/homepage/design7/dload.html)

Do you have any skins in /usr/share/mplayer/Skin/default/ ?

---

### Post by Timokl on 2006-06-11
Dear Angkor,

thanks for your help. I found the solution -- I had a problem with my repositories.  ](*,) 

Now Mplayer works fine. Much better than with Breezy. :D

Bye,
Timo

---

### Post by Satyagraha on 2006-06-12
What was the problem with the repositories? Because I'm having the same problems.

---

### Post by ellingb on 2006-06-12
I don't know about the repositories, but I removed Mplayer and installed it again, and now it works fine.

BR

Elling

---

### Post by Timokl on 2006-06-13
[QUOTE=Satyagraha]What was the problem with the repositories? Because I'm having the same problems.[/QUOTE]

One of the repository adresses did not work, because the repository listing was not compressed, and so apt-get did not receive the list in a way it expected and left out that one list. (Hope this is understandable. :))

Here's my new sources.list which works:

```
deb http://de.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper main restricted

deb http://de.archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper universe multiverse

deb http://de.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates main restricted

deb http://de.archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu dapper-updates universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse

deb http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://de.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

```

Bye,
Timo

---

### Post by Satyagraha on 2006-06-13
Still no luck! Changed my sources.list to your sources.list, but I'm getting the same error. :(

---

### Post by Yleeyas on 2006-06-13
Hi Satyagraha, 

Did you try reinstalling the mplayer-skins? I used Synaptic for this and it cleared things up nicely. (Thanx Angkor)

Yleeyas

---

### Post by Satyagraha on 2006-06-13
After reinstalling mplayer-skins MPlayer works again. Thanks a lot guys! :D

---

### Post by binks on 2006-06-13
[QUOTE=Satyagraha]After reinstalling mplayer-skins MPlayer works again. Thanks a lot guys! :D[/QUOTE]


thanks this also worked for me

---

### Post by kumbakara on 2006-06-14
Yes. Reinstalling mplayer-skins solved the skin not found issue of gmplayer.
tnx.

---

### Post by dnccnd on 2006-06-14
It worked also for me!

Thanks a lot

---

### Post by nanotube on 2006-06-22
worked for me, too. (but i used aptitude instead of apt-get.)

---

### Post by routerstu on 2006-07-15
i had to reinstall skins as well to get it to work.

hmmmm

---

