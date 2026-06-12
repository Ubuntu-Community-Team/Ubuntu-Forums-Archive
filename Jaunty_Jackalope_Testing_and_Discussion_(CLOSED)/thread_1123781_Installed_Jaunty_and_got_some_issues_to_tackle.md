---
title: "Installed Jaunty and got some issues to tackle"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kivech on 2009-04-12
Hi all,

I figured I just toss my problems in one post for starters. Sorry if there is a double one in there, but I couldn't find any specific answers to my problems.

1) Printer: Epson Stylus Office BX300F seems only partly supported.
Even though there is a driver for it, it doesn't print or respond to any commands from the printer control interface. The scanner is not recognized by Xsane at all. Shame of a new printer I would say. Makes me feel that it might be an authorization problem somewhere since it keeps complaining that it might not be plugged in, while it in fact works fine in Windows.

[COLOR="Red"]Got this one printing now. This is how I solved it: [http://ubuntuforums.org/showthread.php?p=7059909#post7059909]("http://ubuntuforums.org/showthread.php?p=7059909#post7059909") Now I still need a solution for the scanner part of this one.[/COLOR]

2) Webcam: Philips webcam which was supported just fine in previous versions of Ubuntu now suddenly is not even found anymore. No more video calls for me at this point. Any ideas how I can figure out what's the problem here?

3) Bugs in general: I'm a tad worried since I still run into countless bugs so close to release (all software related). I for sure don't have the time to file them all, but some I will (once I have some time).

4) Video: any idea when we will get the ATI proprietary drivers for Jaunty? Or could I attempt to manually install the latest ATI ones from their website (done it before, so I'm not afraid to do it). Does anyone have any positive results with ATI's packages on Jaunty?

5) Audio: I'd like to turn off the PC speaker (I always do) but in the audio config screen I cannot anymore (there used to be a tick box to turn it off if I remember correctly). Is there another way in which we can turn off the PC speaker that I might have missed?

6) Tried to get Gcompris running but it won't. Is this just a regular bug or should it be working out of the box? I'm getting this error upon launch:
> ** (process:3533): WARNING **: Binary relocation disabled
package_data_dir         = /usr/share/gcompris/boards
package_locale_dir       = /usr/share/locale
package_plugin_dir       = /usr/lib/gcompris
package_python_plugin_dir= /usr/share/gcompris/python
Infos:
   Config dir '/home/marc/.config/gcompris'
   Users dir '/home/marc/My GCompris'
   Database '/home/marc/.config/gcompris/gcompris_sqlite.db'
Exception ImportError: 'No module named Numeric' in 'garbage collection' ignored
Fatal Python error: unexpected exception during garbage collection
Aborted (core dumped)


7) The Disk Usage Analyser gives wrong readings, reporting certain partitions to be used for the full 100% indicating a size much smaller than their real size. Is this potentially a configuration issue or could this be a bug of the program?

8) Lastly: installed VLC video player. I use two monitors and put the player on one and work on the other (so the kids can watch stuff while being with me while I'm working on my PC). Problem is that going from one track to the next it basically resets its display screen, making it play on the other screen than the one I launched it from. Never noticed this before in software. Anyone know how I can potentially fix this?

9) Nearly forgot: Google Earth is unusable due to the way it generates video (remember I have no proprietary ATI driver atm). Is there a way to get it to display so I can use it?

Well, I recon that is enough for now. Thanks in advance for any help you guys can give me. Meanwhile I will keep looking for solutions myself, and if I find one I will make sure to post it here.

Kivech

---

### Post by hfw on 2009-04-18
I have also had issues with gcompris in Jaunty.  Very disappointing to my 4 year old daughter.  Hoping there is some way to get it working.

-hal

---

### Post by timrichardson on 2009-04-20
gcompris on jaunty: it works if you install first another package: python-numeric

the gcompris included in jaunty is badly packaged (this dependency should be included) and it's out of date (python-numeric is not needed in newer releases).

Hopefully it's fixed soon. I normally use debian but installed Jaunty (RC1) on my son's laptop to see how Ubuntu is going ... He's four ... loves gcompris.

---

### Post by hfw on 2009-04-20
Thanks for the tip.  I will give it a shot when I boot into Ubuntu later today.  My daughter will be glad to hear it's fixed.

---

