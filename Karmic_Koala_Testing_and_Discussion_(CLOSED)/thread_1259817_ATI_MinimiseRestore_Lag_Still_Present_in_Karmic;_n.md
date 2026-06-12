---
title: "ATI Minimise/Restore Lag Still Present in Karmic; no workaround?"
date: 2009-09-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by JCoster on 2009-09-06
Hey guys,
I've never run an alpha version of Ubuntu before so sorry if this is the wrong place to post but..
I thought i'd upgrade from Jaunty just to fill an evening and to try and fix a few issues I was having, primarily with sound drivers which I am delighted to say is now all sorted.
However, I was one of many that suffered from the 2-3second lag between minimising and restoring windows with the ATI drivers which was solved by the 'xserver-no-backfill' patch [reference: [here]("http://ubuntuforums.org/showthread.php?t=1172875")].
However, since upgrading I assume that xserver has been upgraded because the patch now doesn't work and the lag is back.
I'm not overly bothered about it because I can live without desktop effects, just they'd be nice in the long-run.  
So yeah, I just tried to apply the patch but it wasn't working (I'm assuming because it's built for Jaunty) so at the moment I am unable to find a workaround. 
I'm on ATI HD3650 card with the restricted drivers.
I may be being stupid but I just thought this could help someone who's working on Karmic.  

Other than this problem, nice work!  Much smoother and more pleasant than my experience with Jaunty, although that may be down to having no desktop effects...

Cheers

---

### Post by zoomy942 on 2009-09-07
I had the same problem with my ati 4670. I gaurentee there is a fix because I applied it and mine works fine. When I get home later I will dig it up for you.

---

### Post by JCoster on 2009-09-07
Brilliant; thanks for your help.

---

### Post by JCoster on 2009-09-07
Also, I know this is somewhat off-topic but when you get around to replying then please could you let me know how your video performance is with this card?  

With Jaunty I experienced a great deal of tearing no matter what I tried when desktop-effects were enabled.  I'm trying to use VLC.

Thanks

---

### Post by Sophont on 2009-09-08
> **zoomy942 said:**
> I had the same problem with my ati 4670. I gaurentee there is a fix because I applied it and mine works fine. When I get home later I will dig it up for you.

4670? Perfect - is the freshly released fglrx working for you?
Wait - you probably have the desktop version?

---

### Post by JCoster on 2009-09-08
Nah I have the laptop version in a Sony Vaio VGN-FW31ZJ. I ran a sudo update-manager yesterday and updated everything it suggested. I only upgraded on Sunday. Are you using the ATI or the restricted driver?
Thanks

---

### Post by zoomy942 on 2009-09-08
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1245303](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1245303)

the second post solved it for me

---

### Post by JCoster on 2009-09-08
Thanks.
I have updated to the latest fglrx driver and have previously installed the patch so I haven't been asked to upgrade again.
However, I cannot enable desktop effects.  Under 'Hardware Drivers' it says that the FGLRX driver is activated but not in use, and when I attempt to enable desktop effects it just tells me that 'desktop effects could not be enabled.'

---

### Post by flowerdealer on 2009-09-08
Hi, is the patch available for karmic, or can I use the jaunty one?

---

### Post by Sophont on 2009-09-09
> **JCoster said:**
> Thanks.
I have updated to the latest fglrx driver and have previously installed the patch so I haven't been asked to upgrade again.
However, I cannot enable desktop effects.  Under 'Hardware Drivers' it says that the FGLRX driver is activated but not in use, and when I attempt to enable desktop effects it just tells me that 'desktop effects could not be enabled.'

That answers my question. Thanks.

I tried the fglrx right after I installed KK on my new XPS 16 a week ago. That lead to a scrambled screen and I had to manually remove the fglrx driver - so I'm back on the default free driver. Which works great for all non-3D stuff, but want my games back. :-)

Then a few days ago the beta of the next fglrx driver got included and success messages came in. But looking at release notes only the non-Mobility 4670 is listed as supported. It doesn't appear under the Mobility section. I was hoping that that's just a mistake (the 2 variants seem to be *very* similar). That's why I was hoping to hear that you have the Mobility 4670 running with the shiny new fglrx.

---

### Post by JCoster on 2009-09-09
Right I'm really not getting anywhere with this.

At the moment I have the latest fglrx driver (installed by removing the old one then 'sudo apt-get install xorg-driver-fglrx' and then editing my xorg.conf to use the fglrx driver.

The desktop effects are enabled on 'normal' settings.

The xserver-no-backfill PPA source is added to my software sources and I have run an update but I'm still experiencing the restore lag.

I think the problem is either:
a) The patch isn't compatible with Karmic
b) When i installed the patch on Jaunty it updated xserver, then upgrading to Karmic installed a new version of xserver which removed the patch but Ubuntu thinks it's still installed and therefore won't install the upgrade.

What happened with Jaunty was that I installed the patch before a PPA was released and I actually downloaded the patch and then installed it through the terminal, so what I'd ideally like to do is remove the patch and then reinstall it.

Any ideas how to do this?  Or other suggestions whatsoever?

---

### Post by JCoster on 2009-09-10
Right, I've identified the problem.  
I just downloaded the 'xserver-xorg-core_1.6.0-0ubuntu14.1~nobackfill~1_amd64.deb' package from the PPA and attempted to run it with GDebi Package Installer and it won't install because 'Error: A later version is already installed.'
I guess it's just not compatible with the current version of xserver in Karmic.
Thoughts?

---

### Post by JCoster on 2009-09-10
Don't know whether this will help, but the version of XServer the patch is built for is 1.6.0-0, whilst the latest version in the repos is 1.6.3-1; hence the incompatibility.

---

### Post by JCoster on 2009-09-14
*sigh*

this is the last time i'll try...  I understand that people get frustrated and if people don't reply it's because they don't know but..

*bump*

---

### Post by VMC on 2009-09-14
Have you looked at [**LP**]("https://launchpad.net/ubuntu") for any related bug reports or file you yourself. I don't have ATI but I have seen plenty of solutions suggested on this forum.

---

### Post by JCoster on 2009-09-14
Hey thanks. 
I've taken a look but can only find the bug related to Jaunty; nothing about Karmic, and all the posts just recommend the xserver-no-backfill patch which just isn't compatible the karmic version of xserver.
JC

---

### Post by screaminj3sus on 2009-09-18
Yeah it would be really nice if we could get this patch for karmic, minimise lag is still here.

The **only** solution for ati/compiz restore from minimize lag is this patch.

---

### Post by screaminj3sus on 2009-09-19
This seems sort of fixed for me now, still some delay, not as much with the latest karmic updates.

Still wish there was a no backfill patch for karmic, felt even more responsive with it.

EDIT: I have found a decent solution, since both compiz and metacity compositer have this lag, I tried installing mutter from the repos, it works great! no lag at all and it doesn't tear like compiz/metacity either!

I recommend you try it.

---

### Post by JCoster on 2009-09-20
I confirm that the latest driver does improve the response time but it's still unusable on a production system.

I'd try mutter but I can't find much information or documentation on it and I'm trying to keep this installation as clean as possible...  

I just hope they come up with a fix for this soon since so many people seem to be effected by it.

---

### Post by Longinus00 on 2009-09-20
> **screaminj3sus said:**
> This seems sort of fixed for me now, still some delay, not as much with the latest karmic updates.

Still wish there was a no backfill patch for karmic, felt even more responsive with it.

EDIT: I have found a decent solution, since both compiz and metacity compositer have this lag, I tried installing mutter from the repos, it works great! no lag at all and it doesn't tear like compiz/metacity either!

I recommend you try it.

Is there anyway to get workspaces working in mutter without having to use gnome-shell?

---

### Post by screaminj3sus on 2009-09-20
> **Longinus00 said:**
> Is there anyway to get workspaces working in mutter without having to use gnome-shell?

tbh I don't use workspaces, so I'm not sure.

its weird, some things like nautilus windows(doesn't lag but sometimes skips minimize animation), pidgin ect... don't have any minimize lag, but firefox is just atrocious.

---

### Post by uBeer on 2009-09-20
> **screaminj3sus said:**
> tbh I don't use workspaces, so I'm not sure.

its weird, some things like nautilus windows(doesn't lag but sometimes skips minimize animation), pidgin ect... don't have any minimize lag, but firefox is just atrocious.

The lag is proportional to the size of the window that is displayed. Probably your firefox window fills almost your whole screen while pidgin is a lot smaller.

But let's hope somebody makes a fix for this...

---

### Post by screaminj3sus on 2009-09-21
I honestly don't know why they don't include the fix, all they have to do it put the no backfill patch in the repos, by default the regular xorg is installed, but when you install fglrx from the repos it also installs the no backfill xorg. At the very least it should just be in the repos.

---

### Post by Enigmatic on 2009-09-27
Is there a Launchpad bug filed for this? I've noticed the delay myself, and it's very frustrating.

---

### Post by krazyd on 2009-09-28
> **screaminj3sus said:**
> I honestly don't know why they don't include the fix, all they have to do it put the no backfill patch in the repos, by default the regular xorg is installed, but when you install fglrx from the repos it also installs the no backfill xorg. At the very least it should just be in the repos.

it's not because there are security issues. Like if your sensitive personal info is in the buffer, it can appear as garbage on the screen with that patch.

the real bug here is fglrx. and that is being addressed by the open-source radeon driver which provides 2D and (experimental, but fast-improving) 3D.

---

### Post by JCoster on 2009-09-28
> **Enigmatic said:**
> Is there a Launchpad bug filed for this? I've noticed the delay myself, and it's very frustrating.

The relevant Launchpad bug is [here](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186), but it's just an extension of the one filed for Jaunty.

---

### Post by screaminj3sus on 2009-09-28
But still why not put the backfill patch in the repos for people who dont care about that? Its also EXTREMELY unlikely garbage on screen would show any readable info, and I used this patch in jaunty and got no on screen garbage.

---

### Post by peppot on 2009-09-29
I grabbed the .debs of the jaunty packages and forcibly installed them. Had to remove the xorg -dev package though for its deps to work.  Now my package system is borked, but desktop is usable again. Will have to live with this until someone makes a karmic no-backfill package

---

### Post by screaminj3sus on 2009-09-29
We srsly need some damn karmic packages. If karmic goes final without any kind of woraround/fix for this I will be thouroughly pissed.

---

### Post by JCoster on 2009-10-01
So here we have it...  Felix Kuehling has developed a patch over at Launchpad which resolved the problem.

The patch can be downloaded [here](http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch).

The instructions to install are as follows:
```
sudo apt-get build-dep xorg-server
apt-get source xorg-server
cd xorg-server-1.6.3
patch -p1 < /path/to/xserver-xorg-backclear.patch
debuild
cd ..
sudo dpkg --install xserver-xorg-core*.deb
```

I had to "apt-get install devscripts" in order to get the debuild package, which upon running failed with the following output:
```
Now signing changes and any dsc files...
 signfile xorg-server_1.6.3-1ubuntu7.dsc Loïc Minier <loic.minier@ubuntu.com>
gpg: skipped "Loïc Minier <loic.minier@ubuntu.com>": secret key not available
gpg: /tmp/debsign.EVxIHZtW/xorg-server_1.6.3-1ubuntu7.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1255:
running debsign failed
```

However, I ignored this and finished off the instructions, rebooted, enabled desktop effects and the lag is totally gone!

Many thanks to Felix for the patch and instructions.

The related Launchpad post can be found [here](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/234).

Let me know how you get on, but it's fixed on my HD3650!

---

### Post by filologen on 2009-10-01
Thanks a lot for the instructions! I just tried this on my Thinkpad T500, and everything seems to work fine :-)

---

### Post by Enigmatic on 2009-10-01
That worked wonderfully!

---

### Post by screaminj3sus on 2009-10-01
> **JCoster said:**
> So here we have it...  Felix Kuehling has developed a patch over at Launchpad which resolved the problem.

The patch can be downloaded [here](http://launchpadlibrarian.net/32728179/xserver-xorg-backclear.patch).

The instructions to install are as follows:
```
sudo apt-get build-dep xorg-server
apt-get source xorg-server
cd xorg-server-1.6.3
patch -p1 < /path/to/xserver-xorg-backclear.patch
debuild
cd ..
sudo dpkg --install xserver-xorg-core*.deb
```

I had to "apt-get install devscripts" in order to get the debuild package, which upon running failed with the following output:
```
Now signing changes and any dsc files...
 signfile xorg-server_1.6.3-1ubuntu7.dsc Loïc Minier <loic.minier@ubuntu.com>
gpg: skipped "Loïc Minier <loic.minier@ubuntu.com>": secret key not available
gpg: /tmp/debsign.EVxIHZtW/xorg-server_1.6.3-1ubuntu7.dsc: clearsign failed: secret key not available
debsign: gpg error occurred!  Aborting....
debuild: fatal error at line 1255:
running debsign failed
```

However, I ignored this and finished off the instructions, rebooted, enabled desktop effects and the lag is totally gone!

Many thanks to Felix for the patch and instructions.

The related Launchpad post can be found [here](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/351186/comments/234).

Let me know how you get on, but it's fixed on my HD3650!
Worked perfectly for me, thanks! (mobility 2600)

---

### Post by PauGNU on 2009-10-02
Hi

I'm compiling it now on my laptop (amd64). These packages that are generated can be used on other 64bit systems?. 

By the way, I also had to install pgp (I got an error related to the absence of this package).

Thanks a lot!

---

### Post by screaminj3sus on 2009-10-02
I got that error as well but you can safely ignore it and it still works.

BTW does anyone know how to make update manager stop offering to update xorg-server? I locked it in synaptic and did sudo hold but it still shows up in update manager and I don't want to accidentally update it and lose my patch.

---

### Post by filologen on 2009-10-02
> **screaminj3sus said:**
> BTW does anyone know how to make update manager stop offering to update xorg-server? I locked it in synaptic and did sudo hold but it still shows up in update manager and I don't want to accidentally update it and lose my patch.

I have the same problem and would also like to find a solution.

---

### Post by Superpiffer on 2009-10-02
i've made a deb with version 1.6.3-1ubuntu8 bypassing temporarily this problem (at least until the next version)
[http://www.megaupload.com/?d=T85A06NG](http://www.megaupload.com/?d=T85A06NG)

---

### Post by JCoster on 2009-10-04
> **Superpiffer said:**
> i've made a deb with version 1.6.3-1ubuntu8 bypassing temporarily this problem (at least until the next version)
[http://www.megaupload.com/?d=T85A06NG](http://www.megaupload.com/?d=T85A06NG)

It's worth noting that for anyone who wishes to try this .deb, it's compiled for i386 only.

---

### Post by praveenmarkandu on 2009-10-04
okay, so here is the thing. the only reason why i want compiz is because it makes the notify-osd look a whole lot better. i dont care about wobbly windows or how the windows maximize and minimize.

is there a way to switch off the maximize and minimize animations. is there also a way to switch the "switcher" (alt-tab) to something the non-compiz one. i've played around with ccsm and turning off animations doesnt do anything. also if i disable the static switcher it doesnt default back to the non-compiz way.

i dont want to patch my system because i dont want to reinstall if something goes wrong. also the patch is not gonna be permanent. much help would be appreciated.

---

### Post by uBeer on 2009-10-05
> **praveenmarkandu said:**
> okay, so here is the thing. the only reason why i want compiz is because it makes the notify-osd look a whole lot better. i dont care about wobbly windows or how the windows maximize and minimize.

is there a way to switch off the maximize and minimize animations. is there also a way to switch the "switcher" (alt-tab) to something the non-compiz one. i've played around with ccsm and turning off animations doesnt do anything. also if i disable the static switcher it doesnt default back to the non-compiz way.

i dont want to patch my system because i dont want to reinstall if something goes wrong. also the patch is not gonna be permanent. much help would be appreciated.

If you just want the notify-osd to look good you could as well try to use the metacity compositer. That works really well with the open source driver. Actually even better because there is decent VSync (especially noticeable when using Gnome Do Docky).

So if you do not need power savings (and 3D on newer ati cards) then you could consider trying out the open source drivers with the metacity compositor.

To enable:
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
```

---

### Post by tom66 on 2009-10-05
I've found a workaround. Install the following PPA. Fixed everything for me. However, I've still got suspend bugs on my laptop with 9.04, so I'm sticking with 8.10 for now. 

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

I don't notice any corruption so it works for me!

---

### Post by Amaranth on 2009-10-05
The reason this new patch is not being applied even though it at first glance appears to fix the problem for fglrx without causing problems for others is that it does in fact cause problems for others. Apparently with this patch everyone gets 1-2 seconds of black when opening a menu while without it the menu pretty much opens immediately.

Just wanted to let you know we're not intentionally making this worse for you guys. It's just that this these patches only fix one (in comparison) minor bug for fglrx while adding rather bad bugs for everyone else. In the end AMD just needs to fix the driver.

---

### Post by praveenmarkandu on 2009-10-05
> **uBeer said:**
> If you just want the notify-osd to look good you could as well try to use the metacity compositer. That works really well with the open source driver. Actually even better because there is decent VSync (especially noticeable when using Gnome Do Docky).

So if you do not need power savings (and 3D on newer ati cards) then you could consider trying out the open source drivers with the metacity compositor.

To enable:
```
gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true
```


thanks for this. i didnt know metacity had a composite option. however i have already installed the ati proprietary drivers. i might do a roll-back if i feel like it. composite looked and worked fine except for watching video. Vsync was totally non-existent (thanks to the damn ati drivers) it was even worse the screen tearing i normally have.

---

### Post by JCoster on 2009-10-05
> **tom66 said:**
> I've found a workaround. Install the following PPA. Fixed everything for me. However, I've still got suspend bugs on my laptop with 9.04, so I'm sticking with 8.10 for now. 

[https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill](https://edge.launchpad.net/~ubuntu-x-swat/+archive/xserver-no-backfill)

I don't notice any corruption so it works for me!

This only works on Jaunty, not Karmic.

---

### Post by Marat89 on 2009-10-07
> **Superpiffer said:**
> i've made a deb with version 1.6.3-1ubuntu8 bypassing temporarily this problem (at least until the next version)
[http://www.megaupload.com/?d=T85A06NG](http://www.megaupload.com/?d=T85A06NG)

sry i have a question:
if i install your package, Update-Manager wouldnt offer me any xserver updates anymore? and after installing this package, is the bug fixed again?

---

### Post by ELD on 2009-10-07
Has anyone contacted AMD to get an answer about this? Since it is a bug with their drivers, they should be notified about it.

I actually turn compiz off due to this bug (yes i know i can tweak the settings to just turn off effects for minimize...which i will get around to eventually so i can have everything else all pretty looking).

---

### Post by praveenmarkandu on 2009-10-07
> **ELD said:**
> (yes i know i can tweak the settings to just turn off effects for minimize...which i will get around to eventually so i can have everything else all pretty looking).


you can do this? i've tried using ccsm and disabling the animations plugin but it still minimizes and maximizes compiz style. whats wrong?

---

### Post by ELD on 2009-10-08
> **praveenmarkandu said:**
> you can do this? i've tried using ccsm and disabling the animations plugin but it still minimizes and maximizes compiz style. whats wrong?

There are many options in the settings, i have done it before.

---

### Post by runesvend on 2009-10-11
Just to let people know, I just tested Felix' patch with xorg-server_1.6.4-2ubuntu1 and it works.

Also, I made a little script (based on Felix' instructions) for getting the xorg source, patching it and installing the patched xorg-server.

**NOTE:**
1. The script needs to be run as root. So all commands in the script will then be run as root, which really is not necessary. But I don't know how to run only some commands in a script as root, without prompting the user for his password when the script runs (which kind of takes away the automatic-ness of it all).

2. Since Felix' patch is made for xorg-server_1.6.3-1ubuntu4, applying it to any other version of xorg-server than this is not guaranteed to work. But as mentioned, it *does* work with xorg-server_1.6.4-2ubuntu1.

---

### Post by !@!@! on 2009-10-11
I successfully installed the patched xorg on 64 bit, with xorg-server_1.6.4-2ubuntu1.

If anyones interested in downloading the amd64 packages, here is a link!
[http://www.zshare.net/download/668133168b826cca/](http://www.zshare.net/download/668133168b826cca/)
[http://uppit.com/v/K6P818CF](http://uppit.com/v/K6P818CF)

:guitar:

---

### Post by Superpiffer on 2009-10-16
i found this nwe ppa for karmic! :D
[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

---

### Post by !@!@! on 2009-10-16
> **superpiffer said:**
> i found this nwe ppa for karmic! :d
[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

awesome!!! :d

---

### Post by PauGNU on 2009-10-21
Thanks Superpiffer!!

---

### Post by godhika on 2009-10-21
> **Superpiffer said:**
> i found this nwe ppa for karmic! :D
[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

:guitar: thanks a lot

---

### Post by JCoster on 2009-10-22
> **Superpiffer said:**
> i found this nwe ppa for karmic! :D
[https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/](https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/)

Brilliant find!

A month and a half later and I can finally mark it as solved!

Cheers for all your discussion guys.

---

### Post by runesvend on 2009-10-26
***EDIT:** Hm. It seems this "trick" doesn't work. The two packages are just kept back. Today, when I removed the "/etc/apt/preferences" file, they were update to the ppa1-version anyway. So never mind :).*


Update Manager just updated the xserver-xorg-core and xserver-xorg-core-dbg packages to version "2:1.6.4-2ubuntu4" on my system. That is, the official version and not the "2:1.6.4-2ubuntu4~ppa1"-version from Mathias Weyland's [xserver-nobackfill]("https://launchpad.net/~launchpad-weyland/+archive/xserver-nobackfill/") repository.
I *think* I found out how to amend this, however.

First I installed the patched versions of xserver-xorg-core and xserver-xorg-core-dbg again:

> apt-get install xserver-xorg-core=2:1.6.4-2ubuntu4~ppa1 xserver-xorg-core-dbg=2:1.6.4-2ubuntu4~ppa1

I then created the file "/etc/apt/preferences" in which I put the following text:

> Package: xserver-xorg-core
Pin: version *ppa1
Pin-Priority: 1001

Package: xserver-xorg-core-dbg
Pin: version *ppa1
Pin-Priority: 1001

This *should* (if I have understood the man-page of *apt_preferences* correctly), prefer versions of xserver-xorg-core and xserver-xorg-core-dbg that end with "ppa1" (which the patched versions do).

I still don't understand, however, why apt-get doesn't "downgrade" xserver-xorg-core and xserver-xorg-core-dbg to version "2:1.6.4-2ubuntu4~ppa1" after putting the above text in "/etc/apt/preferences" and running "apt-get upgrade". This Debian document seems to state that this should happen when the Pin-Priority is set to 1001:

[APT HOWTO - Managing packages]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html")

---

### Post by Enigmatic on 2009-10-27
Your command to install the PPA version didn't work (couldn't find that version).

---

### Post by runesvend on 2009-10-28
I think that's because the PPA version has been updated to 2:1.6.4-2ubuntu5~ppa1. So the following command should work:

> apt-get install xserver-xorg-core=2:1.6.4-2ubuntu5~ppa1 xserver-xorg-core-dbg=2:1.6.4-2ubuntu5~ppa1

However, I think the PPA version should be installed automatically, if you have added the PPA to your software sources list. The reason that the non-patched version was installed on my system was, probably, that the official version was updated, and it took a while for the maintainer of the PPA to compile and update his PPA with the newest version.
Hence why the PPA version installed automatically on my system after updating later without using any tricks.

---

