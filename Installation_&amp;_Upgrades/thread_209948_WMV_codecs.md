---
title: "WMV codecs"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by msteinblock on 2006-07-05
I am trying to play wmv videos.  I have downloaded the w32 codecs with no luck.  I have also tried installing VLC.  Both are playing the audio of the file fine, but no video shows up.  Any ideas as to how to get video??

Thanks!

~Matthew

---

### Post by briguy on 2006-07-05
You need to install the w32codecs package.  Easiest way to do this is with the Automatix script - search for it in these forums and you'll be set.

---

### Post by scxtt on 2006-07-05
is there a (user) specific 'codec directory' for VLC? ... it might look in /usr/lib/win32 by default ... do you have any files in there, since you d/l'd w32codecs?

if so, my only idea involves xine 0.99.3 (wmvs working fine for me) ...

---

### Post by fluffington on 2006-07-05
[QUOTE=briguy]Easiest way to do this is with the Automatix script - search for it in these forums and you'll be set.[/QUOTE]

I would think that typing "sudo apt-get install w32codecs" in the terminal or going through Synaptic would be easier. Automatix does a lot of other stuff, too, but if all you want is one package, it's not worth the extra effort.

---

### Post by msteinblock on 2006-07-05
I already tried all that.  Still no go.

Reading package lists... Done
Building dependency tree... Done
w32codecs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am a newbie here...so go easy on me.  :)  

Thanks again for the help!

Matthew

---

### Post by briguy on 2006-07-05
[quote=fluffington]I would think that typing "sudo apt-get install w32codecs" in the terminal or going through Synaptic would be easier. Automatix does a lot of other stuff, too, but if all you want is one package, it's not worth the extra effort.[/quote]

Provided the correct repositories are enabled in your /etc/sources.list.

---

### Post by fluffington on 2006-07-06
[QUOTE=briguy]Provided the correct repositories are enabled in your /etc/sources.list.[/QUOTE]

Forgot about that part. I guess not everybody adds universe and multiverse right after install like I do.

---

### Post by FredB on 2006-07-06
Indeed. And automatix is **crap** ! It messes every single ubuntu installation I tried it on.

So, I became a command line and Synaptic user, and my system works flawlessly, thanks.

---

### Post by Jagot on 2006-07-06
[QUOTE=fluffington]Forgot about that part. I guess not everybody adds universe and multiverse right after install like I do.[/QUOTE]

w32codecs is not in universe/multiverse.

[https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5](https://help.ubuntu.com/community/RestrictedFormats#head-6c942d1939d97331f96e42b63774003fde7daed5)

---

### Post by msteinblock on 2006-07-06
Anyone have any more suggestions to try?  

I tried downloading/installing the codecs and now i am back to the begining, saying I dont have the proper codecs installed.  When I try to install them, it tells me they are already there.  At least the first time around I got in and it played sound and no video.

Thanks in advance for the help.

~Matthew

---

### Post by fluffington on 2006-07-06
[QUOTE=Jagot]w32codecs is not in universe/multiverse.[/QUOTE]

Actually, the last time I actually installed w32codecs (I was on either Hoary or Warty, can't remember which), it was in Multiverse. Looks like it has since been removed.

---

### Post by scxtt on 2006-07-06
msteinblock,

as i said above - i've got wmv playback using xine 0.99.3 and some codecs from mplayerhq.hu ... it's not hard to do and i can tell you how if you're interested ...

---

### Post by FredB on 2006-07-07
I installed the codecs using the "official" win32 codecs from mplayer site.

1 - downloaded them
2 - unpack them
3 - open a terminal
4 - launched midnight commander with sudo
5-  gone to /usr/local/lib/
6 - created a codecs/ repertory
7 - copied the content of the archive in the newly created directory
8 - quit Midnight Commander

Simpler way than this, please ?

---

### Post by woedend on 2006-07-07
@Fred - Download and double click :p
[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)

@mstein - have you tried mplayer?  or totem?  to use totem, you must install the ugly plugins.  search in synaptic for gstreamer and find the bad and the ugly and install :).

---

### Post by kewldude606 on 2006-07-07
I have the same problem, audio but no video.

I have all of the gstreamer .10 packages and the w32 package.  VLC and mplayer don't like it.

For some videos it works if I am using mplayer-mozilla and then I hit stop adn then play.

Also, VLC has its codecs integrated I think.

---

### Post by FredB on 2006-07-07
> **woedend said:**
> @Fred - Download and double click :p
[http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb](http://www.debian-multimedia.org/pool/main/w/w32codecs/w32codecs_20060611-0.0_i386.deb)

@mstein - have you tried mplayer?  or totem?  to use totem, you must install the ugly plugins.  search in synaptic for gstreamer and find the bad and the ugly and install :).


Wells, it looks like I have the same codecs. But I prefer adding them by hand (win32) than using a .deb package ;)

But for gstreamer, I completely agree with you !

---

### Post by ChrisMcCann on 2006-08-22
From what I can gather from the statistics that WMV3 codec is needed
for many newer wmv movies.  VLC version 0.8.4 only supports WMV1 and WMV2.
There is a new version of VLC, version 0.8.5 that supports WMV3 format.
What I was trying to do was find this version, but it looks like the
ubuntu universe does not have this version  of the package available.  
Does anyone know when the universe team will be upgrading this package?

---

