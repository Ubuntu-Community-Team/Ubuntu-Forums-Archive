---
title: "Could not calculate the upgrade, upgrading 13.10 to 14.04 LTS"
date: 2014-04-20
forum: Installation &amp; Upgrades
---

### Post by gillk on 2014-04-20
I am completely stymied by this error. The bottom line readout from do-release-upgrade is:

```
Could not calculate the upgrade 


An unresolvable problem occurred while calculating the upgrade. 


This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

```

/var/log/dist-upgrade/main.log tells me:


2014-04-20 11:12:19,596 ERROR Dist-upgrade failed: 'E:Unable to correct problems, you have held broken packages.'

I've tried removing ppa's, all 3rd party libs, purging, removing, rebooting. I've searched for held packages - nothing.  

Any ideas?

---

### Post by capagira on 2014-04-21
> **gillk said:**
> 
Any ideas?

In my case it was because of cinnamon [not yet supported in trusty];
after removing it I could upgrade
then I reinstalled it from the nightly-build repo

hope this can help you

---

### Post by gillk on 2014-04-21
Thanks for the reply. Alas, I'm not running Cinnamon. Can you tell me how you went about determining that that was the problem? Or was it just trial and error?

Also - how do you like Cinnamon?

---

### Post by capagira on 2014-04-22
check the log files in [COLOR=#333333][FONT=Ubuntu Mono]/var/log/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu Mono]dist-upgrade
[/FONT][/COLOR]and specifically [COLOR=#333333][FONT=Ubuntu Mono]apt.log
[/FONT][/COLOR]
see also:
[https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1279762](https://bugs.launchpad.net/ubuntu/+source/cinnamon/+bug/1279762)

other cases are related to extreme xorg packages


Cinnamon is my fav graphical environment
but I'm using gnome-shell 3.10 too

---

### Post by ibjsb4 on 2014-04-22
> [COLOR=#000000]E:Unable to correct problems, you have held broken packages.[/COLOR]

Try the fix broken package command

```
sudo apt-get -f install
```

---

### Post by gillk on 2014-04-22
Yeah, I tried -f install before posting this. No dice. 

```
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


... BUT apt.log is a bit more promising. Am I reading this right that all these packages are broken?

```

$ grep Broken apt.log
Broken libqt5core5a:amd64 Breaks on libqt5core5 [ amd64 ] < 5.0.2+dfsg1-7ubuntu11.1 > ( libs ) (< 5.2.0+dfsg~)
Broken cups-filters:amd64 Conflicts on foomatic-filters [ amd64 ] < 4.0.17-1ubuntu1 > ( universe/text )
Broken libharfbuzz0b:amd64 Conflicts on libharfbuzz0a [ amd64 ] < 0.9.19-1 > ( libs )
Broken libclutter-1.0-0:amd64 Breaks on libcogl12 [ amd64 ] < 1.14.0-2 > ( libs )
Broken unity-control-center:amd64 Conflicts on gnome-control-center-unity [ amd64 ] < 1.3+13.10.20131004-0ubuntu1 > ( gnome )
Broken libgoa-1.0-0b:amd64 Conflicts on libgoa-1.0-0 [ amd64 ] < 3.8.3-2 > ( libs )
Broken unity-control-center-signon:amd64 Conflicts on gnome-control-center-signon [ amd64 ] < 0.1.7~+13.10.20130724.1-0ubuntu1 > ( gnome )
Broken evolution-data-server:amd64 Conflicts on evolution-data-server-goa [ amd64 ] < 3.8.5-1ubuntu3 > ( gnome ) (< 3.10.3-0ubuntu2~)
Broken libunity-core-6.0-9:amd64 Conflicts on libunity-core-6.0-8 [ amd64 ] < 7.1.2+13.10.20131014.1-0ubuntu1 > ( libs )
Broken libunity-core-6.0-9:amd64 Conflicts on unity-common [ amd64 ] < none > ( none )
Broken xserver-xorg-video-glamoregl:amd64 Conflicts on xserver-xorg-glamoregl [ amd64 ] < 0.5.1-0ubuntu4.2 > ( x11 )
Broken libcogl-pango12:amd64 Depends on libcogl12 [ amd64 ] < 1.14.0-2 > ( libs ) (>= 1.13.4)
Broken gnome-control-center-datetime:amd64 Depends on indicator-datetime [ amd64 ] < 13.10.0+13.10.20131023.2-0ubuntu1 -> 13.10.0+14.04.20140415.3-0ubuntu1 > ( misc ) (= 13.10.0+13.10.20131023.2-0ubuntu1)
Broken libvlccore5:amd64 Depends on vlc-data [ amd64 ] < 2.0.8-1 -> 2.1.2-2build2 > ( universe/graphics ) (= 2.0.8-1)
Broken libperl5.14:amd64 Depends on perl-base [ amd64 ] < 5.14.2-21build1 -> 5.18.2-2ubuntu1 > ( perl ) (= 5.14.2-21build1)
Broken initramfs-tools:amd64 Breaks on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils ) (< 1.72)
Broken kbd:amd64 Depends on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils )
Broken ubuntu-minimal:amd64 Depends on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils )
Broken initramfs-tools:amd64 Breaks on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils ) (< 1.72)
Broken kbd:amd64 Depends on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils )
Broken ubuntu-minimal:amd64 Depends on console-setup [ amd64 ] < none -> 1.70ubuntu8 > ( utils )
Broken ubuntu-minimal:amd64 Depends on kbd [ amd64 ] < none -> 1.15.5-1ubuntu1 > ( utils )

```

---

