---
title: "Accessing remote files fails, etc"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by pastim on 2012-10-20
I having not having a good time upgrading to 12.10 from 12.04.  I am about to give up and spend another 2 days rebuilding my system on 12.04 from scratch, again.  

Before I do make that decision, I have a very strange problem I'd like to report.

I have a load of flacs & mp3s on a separate system (a vortexbox).  I have installed samba (in the same way as on 12.04) and mounted the remote drive.  I can read small text files on that remote system with no problem.

However, if I try to copy a flac or mp3 to my ubuntu system, or play a track direct from that system using, say, Rhythmbox, the process starts and then locks up.  The process cannot even be killed.

I did this all the time on 12.04.  Nothing has changed on my vortexbox - I can play files on it from a separate laptop. I copied a flac from the vortexbox to my laptop, and tried to play remotely via a share on that laptop.  It still didn't play.  So it is definitely the ubuntu system that's at fault. 

I can download megabytes from the net with no problem, so it doesn't seem to the the network.

Any thoughts out there?

I have also had nightmares with:

- the video (I need nvidia drivers to support unity, which 12.10 says are installed but don't work unless you install some linux source and headers - it took hours to work that out)

- gnome sound button doesn't work (pulse audio vol control does)

- hibernation doesn't work

- reports in libreoffice Base don't work

and I haven't finished trying to set up yet. :frown:

---

### Post by pastim on 2012-10-20
This gets weird.  I can play large movies remotely using my ubuntu desktop from the same vortexbox, so it's not the network or file system itself causing problems.  

I cannot play mp3s or flacs.  I cannot even copy them.  

What could possibly cause that?  Where would I look for a log?

---

