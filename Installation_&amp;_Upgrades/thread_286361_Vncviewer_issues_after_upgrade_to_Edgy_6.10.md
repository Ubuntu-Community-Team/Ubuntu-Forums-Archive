---
title: "Vncviewer issues after upgrade to Edgy 6.10"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by jcoppedge on 2006-10-27
After upgrading to Ubuntu 6.10 with apt-get dist-upgrade (ran several times), I finally have everything installed and working well again.  The only issue I've had is running vncviewer or xtightvncviewer, I've found a similar post regarding fonts but didn't fix my issue?  Anyone else experience the issue and have a solution to share?

$ xtightvncviewer
Warning: Unable to load any usable ISO8859 font
Error: Aborting: no font found

---

### Post by Footer on 2006-10-30
Hey!  I just found your post.  I'm experiencing EXACTLY the same thing using Kubuntu.  I use vncviewer and it worked perfectly on Dapper.  Under Edgy I get this:

vncviewer media_machine:2
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.3 (viewer 3.3)
Password:
VNC authentication succeeded
Desktop name "media_machine:2"
Connected to VNC server, using protocol version 3.3
VNC server default format:
  32 bits per pixel.
  Least significant byte first in each pixel.
  True colour: max red 255 green 255 blue 255, shift red 16 green 8 blue 0
Warning: Cannot convert string "-*-helvetica-bold-r-*-*-16-*-*-*-*-*-*-*" to type FontStruct
Warning: Unable to load any usable ISO8859 font
Warning: Unable to load any usable ISO8859 font
Error: Aborting: no font found

I'd be much obliged if someone has come up with a fix.  I can't tell if this is on the vnc side or the Kubuntu side.  I suspect Kubuntu Edgy though since the only change was going from Dapper to Edgy.

Any ideas?

---

### Post by ddman on 2006-11-09
Quick and dirty fix that worked for me (found after some googling around):
Type this command in terminal
**echo "*popup*font: fixed" | xrdb -merge **
Run vncviewer or tsclient. It should work
Hope that helps.

---

### Post by kotrado on 2006-11-10
It works fine for me :) 
Thanks.

---

