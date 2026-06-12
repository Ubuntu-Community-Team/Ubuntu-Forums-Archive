---
title: "Flash plugin 10 worse than 9?"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by canabal on 2008-10-19
Hey all,

Since upgrading to intrepid I have noticed that less sites work with flash (I am assuming that is because V10).

Some examples:

[http://www.soccernet.com](http://www.soccernet.com) - the video on the right
[http://www.nike.com/nikefree/](http://www.nike.com/nikefree/) - The site does not work at all

Anyone else having these problems? or is it just me?

---

### Post by syko21 on 2008-10-19
Its a problem inherent in Flash player 10. Most websites are still checking for flash player 9 so they think you aren't running one at all. It will fix itself once flash 10 becomes more widespread.

---

### Post by psyke83 on 2008-10-19
> **canabal said:**
> Hey all,

Since upgrading to intrepid I have noticed that less sites work with flash (I am assuming that is because V10).

Some examples:

[http://www.soccernet.com](http://www.soccernet.com) - the video on the right
[http://www.nike.com/nikefree/](http://www.nike.com/nikefree/) - The site does not work at all

Anyone else having these problems? or is it just me?

No, Flash 10 is infinitely better than 9. What you're experiencing is growing pains on the side of those websites: they calculate the version by looking at the string value rather than integers, and mistakenly count 10 as less than 9. 

Flash 10 is now at the final release *for all platforms*, so those sites will have incentive to fix their version detection code pretty fast.

---

### Post by bpl07 on 2008-10-19
Flash performance is much improved on my system compared to hardy and flash 9.  You might wanna try purging flashplugin-nonfree and all libflashplugin.so files, then reinstalling the package through synaptic.

---

### Post by ktp on 2008-10-19
just what i was going to say

---

### Post by sloggerkhan on 2008-10-19
yeah, flash 10 works much better but some sites don't detect it.

---

### Post by FuturePilot on 2008-10-19
It's soooo much better than Flash 9

---

### Post by kansasnoob on 2008-10-19
Try the new Flash 10 Final Release:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Both the .deb and apt versions seem OK for me. I like the apt version. After installing via apt the new plugin shows up as adobe-flashplugin rather than flashplugin-nonfree.

---

### Post by psyke83 on 2008-10-19
> **kansasnoob said:**
> Try the new Flash 10 Final Release:

[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Both the .deb and apt versions seem OK for me. I like the apt version. After installing via apt the new plugin shows up as adobe-flashplugin rather than flashplugin-nonfree.

Please, don't install Flash this way. The Ubuntu packages add a lot of integration and functionality that isn't reflected in the "official" Adobe deb or tarball. Besides, we already have this version in our official repository.

---

### Post by kostkon on 2008-10-19
> **psyke83 said:**
> Please, don't install Flash this way. The Ubuntu packages add a lot of integration and functionality that isn't reflected in the "official" Adobe deb or tarball. Besides, we already have this version in our official repository.
But the package from the repos just downloads the tar.gz from Adobe and installs it. Nothing special.

And if you download the deb from Adobe, you will see that they use the Ubuntu Flash package (albeit a modified one).

---

### Post by psyke83 on 2008-10-19
> **kostkon said:**
> But the package from the repos just downloads the tar.gz from Adobe and installs it. Nothing special.

And if you download the deb from Adobe, you will see that they use the Ubuntu Flash package (albeit a modified one).

Wrong, it does a lot more than that. Check the source and you'll see the scripts; for example, it hooks into nspluginwrapper when required. If a 64bit user tries the Adobe deb, it won't work unless they manually wrap the binary.

It's *never* a good idea to manually install Flash due to the infrastructure Ubuntu has in place.

Aside from creating an unsupported configuration, you will also disable automatic updating of Flash - Adobe provided a deb, not a repository, and the different naming convention of the packages will prevent official updates in the Ubuntu repositories.

---

### Post by MRiGnS on 2008-10-20
Adobe debs are available in Interpid by activating the partner repository alongside Opera 9.

---

### Post by psyke83 on 2008-10-20
> **MRiGnS said:**
> Adobe debs are available in Interpid by activating the partner repository alongside Opera 9.

That's interesting... I guess they have a license to redistribute the binary in the partner repository, but not in multiverse...

---

### Post by plun on 2008-10-20
I think both sites are not Adobe 10 ready.

Sleepy admins, no money....

Going over to DRM protected Silverlight...  ESPN ?

Ask site-support.

---

### Post by philinux on 2008-10-20
Yes very interesting that a license warning appears in the nonfree version.

adobe-flashplugin (partner)
Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a
Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use
the Flash plugin. This package officially supports the following browsers:

Firefox 2.x, Firefox 3.x, SeaMonkey 1.11

flashplugin-nonfree (multiverse)
Adobe Flash Player plugin installer
This package will download the Flash Player from Adobe.  It is a Netscape/Mozilla type plugin.  Any browser based on Netscape or Mozilla can use the Flash plugin.  This package currently supports the following browsers: Mozilla, Mozilla-Firefox, Firefox, Iceweasel, and Iceape.  Also Galeon and Epiphany can use the Flash plugin.  Konqueror can also use the Flash plugin if konqueror-nsplugins is installed.

WARNING: Installing this Ubuntu package causes the Adobe flash plugin to be downloaded from [www.adobe.com]("http://www.adobe.com").  The distribution licence of the Adobe flash plugin is available at [www.adobe.com]("http://www.adobe.com").  Installing this Ubuntu package implies that you have accepted the terms of that licence.

---

### Post by 0xdeadc0de on 2008-10-20
:guitar:I like flash 10 much better, it's WAY more cpu efficient on my machine. With flash 9 if I used any fullscreen video it would run one of my cores at 100% at 1.8ghz and still have choppy video. Youtube, myspace, megavideo, whatever, every site had choppy video. In a laptop that means very hot running, fan running full blast durring the entire movie, shorter lifespan of the fan and battery.

With flash 10 the video's smooth and it only uses 66% of one cpu at 800mhz, no choppyness. 

Although when i first installed it it was crashing a lot, due to nspluginwrapper. When I right clicked on a flash animation it would crash - until I deleted the flash-alternative.so files, but then it would crash when I fullscreened flash videos (But not on right clicks). I noticed it was still running isolated from firefox in npviewer.bin even though nspluginwrapper -l reported nothing at all, so I simply removed nspluginwrapper and I can fullscreen now.

It works great. for me. Honestly, Flashpluginnonfree not mixing well with pulseaudio is the only reason I kept my clients running ubuntu 7.10 instead of putting them on 8.04 without libflashsupport AND nspluginwrapper.

The only other thing I did was setup asound.conf with the 4x3 lines to pump alsa through pulseaudio and install the asound2-plugins

(Note: the reason I had nspluginwrapper installed is because I just migrated from 8.04 to 8.10 beta via update-manager -d - Funny thing though, the beta flash 10 player worked fine inside nspluginwrapper in 8.04 for me.)

---

### Post by bash on 2008-10-20
> **psyke83 said:**
> Please, don't install Flash this way. The Ubuntu packages add a lot of integration and functionality that isn't reflected in the "official" Adobe deb or tarball. Besides, we already have this version in our official repository.

You know what's interesting, according to the maintaner field in Flash .deb from the Adobe site, those .debs are maintained by the Ubuntu Core Devs. So the packages seems to be actually packaged by Ubuntu and just distributed through the Adobe website. Only downside about that .deb is that it is no good for 64-bit users.

---

### Post by kansasnoob on 2008-10-20
> **psyke83 said:**
> Please, don't install Flash this way. The Ubuntu packages add a lot of integration and functionality that isn't reflected in the "official" Adobe deb or tarball. Besides, we already have this version in our official repository.

Point taken. Thank you.

---

### Post by marseille on 2008-10-22
how 2 delete flash 10 if installed via adobe tar?  or did i just ask a really bad question?!:confused:

note:  i read dont install flash that way... 

btw- i crash every few min. now ... didnt use 2 b like that til lately.  started w/ v.9 then 10 ...

---

### Post by 0xdeadc0de on 2008-10-22
> **marseille said:**
> how 2 delete flash 10 if installed via adobe tar?  or did i just ask a really bad question?!:confused:

note:  i read dont install flash that way... 

btw- i crash every few min. now ... didnt use 2 b like that til lately.  started w/ v.9 then 10 ...

in a console:  
sudo updatedb
locate libflashplayer.so
rm /path/to/libflashplayer.so


On my system with the deb installed via synaptics/apt-get I have:

/usr/lib/mozilla/plugin/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin (symlink) -> /usr/lib/flashplugin-nonfree/libflashplayer.so (actual binary plugin)

If I wanted to manually remove flash, i'd simply delete the one file and two symbolic links.

---

### Post by marseille on 2008-10-22
thx 0xdeadc0de :KS

---

### Post by razer22 on 2008-10-23
hi installed flash 10 it was great,then there was a update and it's gone back to flash 9:confused:tryed to uninstall 9 but can't,then i uninstall 10 and then reintalled but it said i have allready installed 10??if i look at ff addons it says flash 9.help me:confused:

---

### Post by philinux on 2008-10-23
> **0xdeadc0de said:**
> in a console:  
sudo updatedb
locate libflashplayer.so
rm /path/to/libflashplayer.so


On my system with the deb installed via synaptics/apt-get I have:

/usr/lib/mozilla/plugin/flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin (symlink) -> /usr/lib/flashplugin-nonfree/libflashplayer.so (actual binary plugin)

If I wanted to manually remove flash, i'd simply delete the one file and two symbolic links.

Also in Firefox ```
about:config
``` if you set the preference **plugin.expose_full_path** to true you can see the location of all plugins in ```
about:plugins
```

---

