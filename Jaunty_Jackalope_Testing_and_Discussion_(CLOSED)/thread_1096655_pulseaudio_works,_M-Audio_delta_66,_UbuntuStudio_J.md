---
title: "pulseaudio works, M-Audio delta 66, UbuntuStudio Jaunty Alpha 6"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by infinite.ailo on 2009-03-15
Yes, PulseAudio recognized my M-Audio Delta 66 card!
When it works, it's not so bad, after all.
Anyone know what has been changed to achieve that?
Never got it to work properly in earlier releases. Tried a few suggestions found on forums and such.

I recommend others to wait for the final release of UbuntuStudio Jaunty, which I believe is due in April.
For myself, I was curious enough to try the alpha release.

Lot's of other issues though.

Jack is giving me problems, as it has in the past, as well.
I am very unsure of the causes, since I am not a Linux-expert, yet.
qjackctl doesn't work at all, so I run jackd from the terminal.

Also, when I upgraded (first from Hardy to Intrepid, then to Jaunty), I kept the realtime kernel without installing the generic one.
I don't know what happend during the upgrade to Jaunty, but my system froze up plenty of times, using all of the system memory as well as a large portion of the swap. I had to turn the power off and reboot using kernel-(recovery) over and over until all the files were installed. 
Finally I got the system to run, with a realtime kernel, but considering my choice of procedure, I don't feel comfortable reporting bugs.

I have had qjackctl not working in the past as well, and I'm guessing it has something to do with UbuntuStudio-specific settings.
If anyone happen to know how to get jack and qjackctl to run on Jaunty, don't be a stranger.

Enough said.
Looking forward to the Jaunty final release.

---

### Post by silentb on 2009-03-15
don't upgrade, reinstall! upgrading nearly always introduces unexpected issues in my experience.

though you might try the cvs version of qjackctl:

```
sudo apt-get build-dep qjackctl

mkdir cvs

cd cvs

cvs -d:pserver:anonymous@qjackctl.cvs.sourceforge.net:/cvsroot/qjackctl login

cvs -z3 -d:pserver:anonymous@qjackctl.cvs.sourceforge.net:/cvsroot/qjackctl co qjackctl 

cd qjackctl

make -f Makefile.cvs

./configure

make -j 2

sudo make install
or
sudo make uninstall
```

---

### Post by markbuntu on 2009-03-16
Jaunty is using pulseaudio 0.9.14 which has major improvements over 0.9.10 which is in Hardy and Intrepid. Jaunty is also using ALSA 1.0.18 which has improved drivers for almost every sound card and chip.

Since you are using ubuntustudio and jack in Jaunty you should give the module pulse-jack a try. The one for pulse0.9.14 is in the Debian experimental repo. I will be giving it a whirl myself sometime this week if I can find the time. There is some directions for using it here, near the end.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by infinite.ailo on 2009-03-16
Thanks for the replies.

This being my first thread on any forum so far has proved to be educational. 

I did try the recommendations given by 'silentb', which led me to begin using cvs as well as taking a closer look at synaptic package manager, and I certainly will look up the 'pulse-jack' module.

The results so far:

qjackctl only works if jackd is initalized through the terminal first. So, I am not able to use the initialization presets on qjackctl, but I am able to use it's connection functions.

I'm guessing there's a bug connected to qjackctl. The gui only shows a maximum of two buttons on the top right corner. No 'close window' button.

I won't pursue this topic any further, unless anyone has any questions for me. Also the description of this thread was not correct, so I'll try to be more minimal and specific in the future.

---

