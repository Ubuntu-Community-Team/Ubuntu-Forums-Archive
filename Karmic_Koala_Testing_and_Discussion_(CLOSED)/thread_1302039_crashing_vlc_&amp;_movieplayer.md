---
title: "crashing vlc &amp; movieplayer"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by BluntedBoyWonder on 2009-10-26
Whenever I try to play an .avi movie my MoviePlayer crashed upon opening. I thought it might be a bug so I downloaded VLC, but this crashes also. 

I installed universe and medibuntu repositories and did update and upgrade.

I've tried several avi's: here's the terminal output:

> 
VLC media player 1.0.2 Goldeneye
[0x8f8c460] main interface error: no interface module matched "globalhotkeys,none"
[0x8f8c460] main interface error: no suitable interface module
[0x8df6a40] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x8df6a40] main libvlc: Start vlc met standaardinterface. Gebruik 'cvlc' om vlc zonder interface te gebruiken.
QPainter::begin: Paint device returned engine == 0, type: 1
[0x91ea1d8] pulse audio output: No. of Audio Channels: 2
QPainter::begin: Paint device returned engine == 0, type: 1
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  105
  Current serial number in output stream:  106
Segmentation fault


Need more info? Please ask for it.

---

