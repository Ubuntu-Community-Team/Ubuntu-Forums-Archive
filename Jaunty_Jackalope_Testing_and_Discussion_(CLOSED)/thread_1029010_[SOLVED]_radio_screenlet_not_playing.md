---
title: "[SOLVED] radio screenlet not playing"
date: 2009-01-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ronacc on 2009-01-02
after some updates a few days ago the radio screenlet stopped playing and drives python to 100% . this started in my old install (updated from intrepid) which I destroyed troubleshooting ipv6 and persists in a fresh install from alternate daily of dec 31 08 (64bit)  filed bug # 313380

---

### Post by lalitgaur on 2009-01-03
i can confirm this on the latest up to date version of jaunty that i have

---

### Post by plun on 2009-01-03
Well...works for me..

But I gave up and is ahead of development...

mplayer from svn including nVidias VDPAU patches...

PulseAudio 100% from GIT...


It just works and uses the Alsa plugin for Mplayer..

[[img]http://ubuntu-pics.de/thumb/7888/start1_ojCCIk.jpg[/img]](http://ubuntu-pics.de/bild/7888/start1_ojCCIk.jpg)

---

### Post by ronacc on 2009-01-03
I don't think this has anything to do with pulseaudio or mplayer or VDPAU . my audio is ok any the station plays fine if I enter the URL directly into mplayer , only the radio screenlet is having a problem .

---

### Post by plun on 2009-01-04
> **ronacc said:**
> I don't think this has anything to do with pulseaudio or mplayer or VDPAU . my audio is ok any the station plays fine if I enter the URL directly into mplayer , only the radio screenlet is having a problem .

The screenlet is just a frontend and its mplayer which is the backend.

It might also be DNS trouble again...:confused:

The vdpau-mplayer script is just an easy way to get mplayer from SVN.

Start **screenlets-manager from terminal** and then Radio and look for errors.

---

### Post by plun on 2009-01-04
Some more test...

This is from menu.xml within /usr/share/screenlets/Radio

```
			<item label="Europe">
			<item label="Antena 3"  id="mms://rdp.oninet.pt/antena3 Antena 3" />
			<item label="Ministry of Sound"  id="http://www.ministryofsound.com/radio/radioplayer/ Ministry of Sound" />
			<item label="BBC Radio 1"  id="http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram BBC Radio 1" />
			<item label="BBC Radio 2"  id="http://www.bbc.co.uk/radio2/realmedia/fmg2.ram BBC Radio 2" />
			<item label="BBC Radio 3"  id="http://www.bbc.co.uk/radio3/ram/r3g2.ram BBC Radio 3" />
			<item label="BBC Radio 4"  id="http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram BBC Radio 4" />
			<item label="BBC Radio 5"  id="http://www.bbc.co.uk/fivelive/live/surestream_int.ram BBC Radio 5" />
			<item label="BBC News"  id="http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram BBC News" />
			<item label="Frequence 3"  id="http://80.65.234.120:8000/ Frequence 3" />
			<item label="Hitz Channel"  id="http://scfire-chi0l-1.stream.aol.com/stream/1074 Hitz Channel" />
			<item label="Hot 108 Jamz"  id="http://scfire-nyk0l-2.stream.aol.com/stream/1071 Hot 108 Jamz" />
			<item label="RMF FM"  id="http://213.251.140.62:8002 RMF FM" />
			<item label="80s Channel"  id="http://scfire-nyk0l-2.stream.aol.com/stream/1040 80s Channel" />
			<item label="Sky FM Jazz"  id="http://scfire-ntc0l-1.stream.aol.com/stream/1010 Sky FM Jazz" />
			<item label="Techno 4ever"  id="http://80.237.156.79:8000/ Techno 4ever" />
			<item label="Digitally imported"  id="http://scfire-nyk0l-1.stream.aol.com/stream/1003 Digitally imported" />
			<item label="Sky FM Top Hits"  id="http://scfire-chi0l-2.stream.aol.com/stream/1014 Sky FM Top Hits" />
			<item label="Smooth Jazz"  id="http://scfire-ntc0l-1.stream.aol.com/stream/1005 Smooth Jazz" />
			<item label="ChroniX Aggression"  id="http://scfire-chi0l-1.stream.aol.com/stream/1039 ChroniX Aggression" />
			<item label="Powerhitz"  id="http://205.188.215.229:8006/ Powerhitz" />
			<item label="Kronehit "  id="http://www.kronehit.at:8081/stream.m3u Kronehit" />
			<item label="Energy 104,2"  id="http://80.237.157.46:8120/listen.pls Energy 104,2" />
			<item label="Welle 1"  id="http://82.150.198.157:8000/welle1.mp3.m3u Welle 1" />
			<item label="Welle 2"  id="http://live-eu.welle1.at:8056/listen.pls Welle 2" />
			<item label="Q-Music"  id="http://www.q-music.be/asx/q_high.asx Q-Music" />
			<item label="NRJ"  id="http://broadcast.infomaniak.net/nrjbe-high.mp3.m3u NRJ" />
			<item label="FUN"  id="http://www.funradio.be/funradiobe-low.high.pls FUN" />
			<item label="Radio Express"  id="http://online.radioexpress.bg:8000/listen.pls Radio Express" />
			<item label="Radio Fresh"  id="http://193.108.24.21:8000/fresh.ogg.m3u Radio Fresh" />
			<item label="Radio Vitosha"  id="http://217.75.128.46:8000/listen.pls Radio Vitosha" />
			<item label="Evropa 2"  id="http://www.play.cz/radio/evropa2-128.asx Evropa 2" />
			<item label="The Voice"  id="http://dix.media.webpartner.dk/voice128 The Voice" />
			<item label="Caz"  id="http://www.garnierstreamingmedia.com/asx/caz.pls Caz" />
			<item label="Capital 95.8"  id="http://mediaweb.musicradio.com/Playlist.asx?StreamID=1 Capital 95.8" />
			<item label="Play Top 40 UK"  id="http://audio4.playradiouk.com:8150/listen.pls Play Top
```



Take a station and run it directly from the terminal


Several are broken.....


```
plun@plun:~$ **mplayer 'http://205.188.215.229:8006/'**

MPlayer dev-SVN-r27960-4.3.3 (C) 2000-2008 MPlayer Team
CPU: Intel(R) Pentium(R) 4 CPU 2.40GHz (Family: 15, Model: 2, Stepping: 7)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled for x86 CPU with extensions: MMX MMX2 SSE SSE2
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing http://205.188.215.229:8006/.
Resolving 205.188.215.229 for AF_INET6...
Couldn't resolve name for AF_INET6: 205.188.215.229
Connecting to server 205.188.215.229[205.188.215.229]: 8006...
Resolving scfire-dtc-aa03.stream.aol.com for AF_INET6...
Couldn't resolve name for AF_INET6: scfire-dtc-aa03.stream.aol.com
Resolving scfire-dtc-aa03.stream.aol.com for AF_INET...
Connecting to server scfire-dtc-aa03.stream.aol.com[205.188.234.3]: 80...
Name   : 1POWER - #1 FOR HITZ & HIP HOP *In HD) www.powerhitz.com
Genre  : hip hop urban rap rnb
Website: http://www.powerhitz.com
Public : yes
Bitrate: 128kbit/s
Cache size set to 320 KBytes
Cache fill:  0.00% (0 bytes)   
ICY Info: StreamTitle='T-Pain - Chopped N Skrewed (Ft Ludacris)';StreamUrl='';
Cache fill: 15.00% (49152 bytes)   
Audio only file format detected.
==========================================================================
Opening audio decoder: [mp3lib] MPEG layer-2, layer-3
mpg123: Can't rewind stream by 1472 bits!
AUDIO: 44100 Hz, 2 ch, s16le, 128.0 kbit/9.07% (ratio: 16000->176400)
Selected audio codec: [mp3] afm: mp3lib (mp3lib MPEG layer-2, layer-3)
==========================================================================
[AO OSS] audio_setup: Can't open audio device /dev/dsp: No such file or directory
AO: [alsa] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
mpg123: Can't rewind stream by 227 bits!
A:  86.6 (01:26.5) of -0.0 (unknown)  0.7% 45% 


```


But what to file a bug against....:confused:

EDIT

Playlist URL can also be wrong and outdated....


EDIT/EDIT

The codecs also.....discussed before as I remembers it  :D

[http://www.mplayerhq.hu/design7/dload.html](http://www.mplayerhq.hu/design7/dload.html)

The codecs pack...  I live in a software patent-free country..:D

---

### Post by ronacc on 2009-01-04
I tried what you sugested but screenlets manager gives no hint of a problem in the terminal also no problems shown in radioscreenlets.log also tried starting the  radio screenlet directly with python in a term again no hint of any problem but python drives the CPU to 100% and stays there until I click on the stop button in the screenlet or kill it (python) from term . I think the problem is that the radioscreenlet don't match the current version of python but I can't prove it .

---

### Post by plun on 2009-01-04
> **ronacc said:**
> I tried what you sugested but screenlets manager gives no hint of a problem in the terminal also no problems shown in radioscreenlets.log also tried starting the  radio screenlet directly with python in a term again no hint of any problem but python drives the CPU to 100% and stays there until I click on the stop button in the screenlet or kill it (python) from term . I think the problem is that the radioscreenlet don't match the current version of python but I can't prove it .

I also just EDIT/EDIT about codecs...discussed before :D

---

### Post by ronacc on 2009-01-04
the specific station I mainly use is bbc news . as I said in an earlier post if I paste the url ( cut from the radio menu.xml ) directly into mplayer it plays fine also plays fine with realplayer so it is not a codec problem or broken station . It had been working fine until an update took it out sometime between dec26 and dec 28 but before I got a chance to TS it I nuked my original jaunty install TSing ipv6 problems and didn't reinstall until jan 1 because the dailys were broken . this is a fresh un tweeked installl from the dec 31 alternate daily .( except for nvidia 180.18 from ppa) .

---

### Post by plun on 2009-01-04
> **ronacc said:**
> the specific station I mainly use is bbc news . as I said in an earlier post if I paste the url ( cut from the radio menu.xml ) directly into mplayer it plays fine also plays fine with realplayer so it is not a codec problem or broken station . It had been working fine until an update took it out sometime between dec26 and dec 28 but before I got a chance to TS it I nuked my original jaunty install TSing ipv6 problems and didn't reinstall until jan 1 because the dailys were broken . this is a fresh un tweeked installl from the dec 31 alternate daily .( except for nvidia 180.18 from ppa) .

OK... it works on 32 bit but not 64 bit and only a problem with
The Radio Screenlet

Its a ram-file

```
<item label="BBC Radio 1"  id="http://www.bbc.co.uk/radio1/realaudio/media/r1live.ram BBC Radio 1" />
			<item label="BBC Radio 2"  id="http://www.bbc.co.uk/radio2/realmedia/fmg2.ram BBC Radio 2" />
			<item label="BBC Radio 3"  id="http://www.bbc.co.uk/radio3/ram/r3g2.ram BBC Radio 3" />
			<item label="BBC Radio 4"  id="http://www.bbc.co.uk/radio4/realplayer/media/fmg2.ram BBC Radio 4" />
			<item label="BBC Radio 5"  id="http://www.bbc.co.uk/fivelive/live/surestream_int.ram BBC Radio 5" />
			<item label="BBC News"  id="http://www.bbc.co.uk/worldservice/meta/tx/nb/live_news_au_nb.ram BBC News" />

``` 


Info for screenlets  and Python packages 
[http://packages.ubuntu.com/jaunty/screenlets](http://packages.ubuntu.com/jaunty/screenlets)


:confused:  Time to sleep....

---

### Post by ronacc on 2009-01-04
I don't know what it being a .ram would have to do with it since mplayer plays the file directly with no problem also watching my nework monitor when it was working I can see the stream that is not happening now , since my synaptic history and apt log for the dates when the update came down that killed it are gone because of the reinstall I can't try to figgure out what specific package did it .  have a good sleep :D

---

### Post by ronacc on 2009-01-05
update to python came down this AM . The radio screenlet now functions normaly . I marked this thread solved .

---

