---
title: "How to install Automatix?"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by ubunKing on 2007-11-03
Hello,, i am a new Linux user.. installed the 7.10 on PC. 
I try to install Automatix, but i don't know how.. 
unlike WINDOWS or MAC, we just download the file, install or drag to the application folder.. Linux got to go to Terminal to type in some stuff... 

I tried to ... but i got this error.. 

"solomon@solomon-desktop:~$ wget [http://beerorkid.com/arnieboy/automatix_6.1_i386.deb](http://beerorkid.com/arnieboy/automatix_6.1_i386.deb)
Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name.
solomon@solomon-desktop:~$ 

what should i do?? 
thank you
UBunKING :)

---

### Post by fdv1 on 2007-11-03
First, a word on installing things in Linux.

There are 2 ways to buy groceries -- go out to the super market, or order them delivered to your door.

Similarly, there are 2 ways to install programs -- go to the website (Windows, Mac, Linux) or tell the OS to bring it to you (Linux).

Installing Automatic can be done by asking the OS to get it for you (apt-get), but let's forget apt-get. Also, let's forget about using the command line for now, too.

Go [here and download the DEB]("http://www.getautomatix.com/apt/dists/gutsy/main/binary-i386/automatix2_2.0.5-7.10gutsy_i386.deb").

Once you download it to your home folder or desktop within your home folder, double click on it. It's that easy!

---

### Post by ubunKing on 2007-11-03
hahahaha. ya.. thanks.. 

i personally like to walk in supermarket, slowly.. looking at the products, enjoying the aircon :) 

Thank you!

---

### Post by ADH on 2007-11-05
Mr. Know-nothing here did the upgrade from 7.04 to 7.10 when prompted, and the upgrade worked without a hitch.  However, I have since found that Automatix, which I installed at the recommendation of a FidoNet friend (the same person who got me to try Ubuntu, and explore Linux) does not work with 7.10.  The Automatix website says to uninstall whatever Automatix installed, then uninstall Automatix, then install the new version.  I can't seem to do the first, as Automatix won't run under 7.10.  I tried to uninstall Automatix, but it doesn't appear under Add/Remove (I searched, but no joy.)  So, any tips as to what I should do?

Thanks as always,

---

### Post by zvacet on 2007-11-05
I think you can uninstall it with synaptic,and if don´t

```
sudo aptitude remove Automatix
```

For programs I don´t know.

---

### Post by ADH on 2007-11-11
Thanks for the tip.

---

### Post by Pumalite on 2007-11-11
Automatic can be completely removed from Synaptic

---

### Post by LosD on 2007-11-19
DO NOT INSTAL AUTOMATIX!

Next upgrade you WILL be screwed.

---

### Post by Pumalite on 2007-11-19
[http://mjg59.livejournal.com/77440.html](http://mjg59.livejournal.com/77440.html)
[http://ubuntuforums.org/announcement.php?f=13/](http://ubuntuforums.org/announcement.php?f=13/)
[http://ubuntuforums.org/showthread.php?t=519872](http://ubuntuforums.org/showthread.php?t=519872)
[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

