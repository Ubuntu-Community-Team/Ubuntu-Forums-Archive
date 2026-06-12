---
title: "Toshiba Satellite - turtle slow after install"
date: 2008-09-24
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2008-09-24
Hi all. Searching for ideas.

Have just done a fresh Xubuntu alternate install on a friend's Toshiba Satellite 2410 with GeoForce4 420 Go video. An old beast but it has 512Mb RAM so there is hope. Things are running okay, except it is incredibly slow and wondering if it is the video drivers. Screens are really slow and programs take forever to open ... not to mention an extremely lengthy boot time.

So, I installed xubuntu-restricted-extras, then nvidia-glx-legacy for the video driver (it has an nvidia NV17) as I thought that would be appropriate for this old machine. Crawling. So I installed 192 updates that were waiting to see if that made a difference. Crawling. So I clicked on the NVidia Restricted Driver in Hardware Drivers and eventually got that ticked and in use. Crawling. Now I can open the Nvidia config GUI but it is too big for the screen which is a clue (can't see things to change all of the options).

It did tell me it was removing the glx-legacy driver in the process of installing glx-new when I ticked the Nvidia restricted driver, but I am wondering if there is some conflict happening. The nvidia-glx shows as installed in Synaptics and the legacy as not though.

As I say, everything is taking forever and this might not be just the vid, but has anyone got any suggestions? I've been at it for a few hours and not ripping the hair out yet but possibly missing something obvious. I will perservere ... :mad:

Thanks in advance ... I am going to add all the info together into a thread I opened when I first started on this in case it helps anyone else with the same lappy. :)

ps: it is online but really slow to open. I could attempt to post some things from the terminal but it might be problematic!

---

### Post by Bucky Ball on 2008-09-24
Where I'm up to now is after screwing around with the graphics drivers for hours thinking that is the problem, I finally installed envyng which identified the vid card (GeForce Go ****?), did its thing which took forever and end result is made no difference at all. I now get logged in fine but am told when I eventually get to the desktop that I am 'starting without administrative privileges.' Boring. The plot thickens.

So: Realise not vid drivers and the machine is running like a slug (extremely slowly) right from the get go. Any donations greatly appreciated.

Update: currently Synaptics Package Manager is booting automatically when I eventually get to the desktop and the desktop is the wrong size for the screen.

Further Update: Have a look at this:
```

/var/cache/apt/archives/nvidia-glx-envy_1%3a96.43.05+2.6.24.503-503.30_i386.deb
/var/cache/apt/archives/nvidia-glx-legacy_71.86.04+2.6.24.13-19.45_i386.deb
/var/cache/apt/archives/nvidia-glx_1%3a96.43.05+2.6.24.13-19.45_i386.deb
/var/lib/dpkg/info/nvidia-glx-dev-envy.list
/var/lib/dpkg/info/nvidia-glx-dev-envy.md5sums
/var/lib/dpkg/info/nvidia-glx-dev-envy.postinst
/var/lib/dpkg/info/nvidia-glx-dev-envy.postrm
/var/lib/dpkg/info/nvidia-glx-dev-envy.preinst
/var/lib/dpkg/info/nvidia-glx-envy.conffiles
/var/lib/dpkg/info/nvidia-glx-envy.list
/var/lib/dpkg/info/nvidia-glx-envy.md5sums
/var/lib/dpkg/info/nvidia-glx-envy.postinst
/var/lib/dpkg/info/nvidia-glx-envy.postrm
/var/lib/dpkg/info/nvidia-glx-envy.preinst
/var/lib/dpkg/info/nvidia-glx-envy.prerm
/var/lib/dpkg/info/nvidia-glx-envy.shlibs
/var/lib/dpkg/info/nvidia-glx-legacy.list
/var/lib/dpkg/info/nvidia-glx-legacy.postrm
```I installed the legacy driver first and if you look at the two bottom lines and the one further up, I am just wondering if they are banging together with the envyng drivers? When the desktop icons first arrive, there are two of everything for a second then all to black, screen comes back up and normal desktop.

Update: After extensive research, this looks like the problem and I will be attempting this fix later today. Again, if anyone is out there, any suggestions welcome and appreciated. :)

[http://ubuntuforums.org/showthread.php?p=4828515](http://ubuntuforums.org/showthread.php?p=4828515)

and:

[http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy](http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy)

Fingers, toes, eyes and legs crossed this works for me!

---

### Post by Bucky Ball on 2008-09-25
Currently ... 

Uninstalled all nvidia drivers and got a normal screen size back rather than the black strip down the right hand side! Think I'm getting closer but things are still *really* slow. The machine is actually working okay except for the crawlingness of it all. Boot up, login; fine. Just slow.

Also, when the desktop is drawing, the desktop icons appear, then another set of icons appear with them, slightly overlapping. Then black screen then back to desktop, one set of icons. 

So, for now, very slow but desktop size fits the screen now. I have envyng installed and last thing I did was remove nvidia drivers with it. nvidia restricted driver in Hardware Drivers is not in use. I am running on the defaults. No nvidia drivers. On boot getting the message "You are in Low Resolution" but have tried process of combination and elimination in there and when I test always get the message:

*'Configuration test failed. Verify Devices and configuration'.*

Hmm :-k

Update: And that is where I'll stop for tonight after many more hours on it. Have figured this:

1/ I can use the 'nv' free driver and things are the right size and shape to fit on the screen but everything is slow.
2/ I can use the 'nvidia' restricted driver, desktop is long and thin so there is a black bar down the right hand side of the screen and the text is incredibly small whilst everything else is incredibly large, the system still works great but ... slow.
3/ EnvyNG is great for completely removing everything nvidia so you know you have a clean slate. Then you can reconfigure xorg.conf with:

There was a fix for number 2 I tried with hex codes from two different pages involving altering the EDID.bin but neither worked. 

[http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy](http://www.r3uk.com/index.php/home/36-useful-information/14-geforce4-420-go-graphics-card-installation-in-ubuntu-710-gutsy)
[http://ubuntuforums.org/showthread.php?t=773391](http://ubuntuforums.org/showthread.php?t=773391)

Either way, I can't neglect the fact that whichever driver I use, the slowness starts right from the progress bar where the sliding block flickers. Interestingly, when I boot the machine, it is into the menu in a flash. Problems only start when leaves grub.

I'll sleep on it ...

Just realised I have been at this for longer that 24 hours and don't think I have ever done this but ...

* bump *

---

### Post by Random-Dude on 2009-06-15
That's odd. I've just installed Xubuntu on my 2410 (which is why this is my 1st post) & it's running fine. I almost laughed when I saw that you had the black stripe, I had that in doze & it took hours (days) to sort out. I haven't had any of the problems you mention with Xubuntu though. It's lightning fast compared to xp (& I've only got 256mb ram), no black stripe any more either. If I saw 'starting without administrative privileges', I'd be reformatting.  Sorry that I've been no help at all. I don't even know what that was that you posted from terminal but if its likely to help then I can post what mine looks like, you'd just need to let me know how to do it.

---

