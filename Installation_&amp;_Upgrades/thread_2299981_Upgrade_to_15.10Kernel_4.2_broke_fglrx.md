---
title: "Upgrade to 15.10/Kernel 4.2 broke fglrx"
date: 2015-10-22
forum: Installation &amp; Upgrades
---

### Post by DanielWEWO on 2015-10-22
Hey guys. So, this morning I updated to 15.10/Kernel 4.2 and apparently, they aren't really working well with the fglrx drivers. I was wondering if anybody knows about a workaround to getting the fglrx drivers working against the 4.2 kernel? Details below:


After installing the new kernel, upon boot, i was given a prompt to choose either a console login, or run the computer in low graphics mode. I had no mouse, so making a choice was quite difficult. So, I just did alt+f1 and logged in. removed all fglrx packages, and rebooted. Display works fine now! But, now if I reinstall fglrx, I get the same issue. I have read elsewhere on the internet that this was a problem, and Ubuntu knew about it, but they pushed 15.10 with kernel 4.2 anyway with no warning for AMD users (that would have been nice.) Oh, well. If you guys know of a workaround let me know! Thanks.


Ubuntu GNOME 15.10
Kernel 4.2.0-16

---

### Post by Bashing-om on 2015-10-22
DanielWEWO; Hello;

Yep, known issue; developers are working on it .
See the release notes:
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)
and the sited bug report.

A million lines of new code added to the kernel ->

[INDENT][INDENT][INDENT]guess something is bound to break
[/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2015-10-22
I'll do some testing either tonight or Saturday.

For the moment:  Did you upgrade or do a fresh install?

Did you uninstall fglrx and remove your xorg.conf before the upgrade?

Have you tried uninstalling fglrx, removing xorg.conf and rebooting, then installing fglrx as described in section 3.1 of the Community ATI wiki in my signature?

If the mainline kernel broke userspace, Linus would have gone ballistic.  I would be terribly surprised if Canonical's kernel modifications broke ATI in userspace.  It could be that AMD's driver is not compatible, which would not be on Canonical.

Canonical and AMD have had a pretty special relationship for years now.

---

### Post by DanielWEWO on 2015-10-22
It was an upgrade, not a fresh install. I didn't uninstall fglrx and delete xorg.conf before the upgrade. Is that good practice? I'll try uninstalling, and removing xorg.conf and reinstalling and I'll post back.

---

### Post by QIII on 2015-10-22
Always uninstall proprietary video drivers before doing a release upgrade.

Just got done testing.  I've confirmed everything in Bashing's link and what I found on Phoronix.  Reinstalling won't work with the 4.2 kernel until Canonical's fglrx package is updated.

---

### Post by DanielWEWO on 2015-10-22
So, yeah you're right. Even after deleting xorg.conf and reinstalling I still got the low resolution mode thing with the black screen.

So the problem isn't the kernel itself, it's just the fglrx package that canonical offers? 

Just curious how quickly something like that would get updated? I'm fine without the graphics card working for a couple weeks. I'm in the middle of my quarter at school and don't have time for games right now anyway =P~

> **Bashing-om said:**
> DanielWEWO; Hello;

Yep, known issue; developers are working on it .
See the release notes:
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes](https://wiki.ubuntu.com/WilyWerewolf/ReleaseNotes)
and the sited bug report.

A million lines of new code added to the kernel ->
[INDENT][INDENT][INDENT]guess something is bound to break
[/INDENT]
[/INDENT]
[/INDENT]



I totally get that, but it's just interesting that they'd push a point release when they know something that's so integral to so many people's computers would make them not boot.

I'm not upset, as I don't need it working at 100% right now, and it took less than a minute to get working again.

---

### Post by QIII on 2015-10-22
How quickly it gets fixed will depend somewhat on how much pressure is applied.  

Please go to the Launchpad [bug report]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888") and click on "... affects me too ..." to turn up the flame.

I just did.

I also gave it a bit more press in a [blog article]("http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go").

---

### Post by Bashing-om on 2015-10-23
@ QIII; :)

> **QIII said:**
> How quickly it gets fixed will depend somewhat on how much pressure is applied.  

Please go to the Launchpad [bug report]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888") and click on "... affects me too ..." to turn up the flame.

I just did.

I also gave it a bit more press in a [blog article]("http://theleftcoastgeek.net/index.php/2-uncategorised/8-fglrx-in-ubuntu-15-10-wily-werewolf-is-a-no-go").

[INDENT][INDENT]you do GooD;
[INDENT][INDENT][INDENT]good deeds done,
[INDENT][INDENT][INDENT][INDENT]dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Jacques_Boulet on 2015-10-23
Will confirm, Kernel 4.2.0 is broken for me in 15.10 with my AMD A6-7400K. I have had to fall back to Kernel 3.19 to use my system. System bombs out when attempting to boot into 4.2.0

>  [drm:amdgpu] [grm:amdgpu_init [amdgpu]] *ERROR* VGACON diables amdgpu kernel modsetting.  

Flashes across the screen real quick before seeing a bunch of text flash across the screen and then everything going black. I hope this gets fixed soon.

---

### Post by QIII on 2015-10-23
In reading around the web, it appears that it is not the kernel that is the problem.

AMD has not released a driver that works with 4.2.

So we're waiting on AMD it seems.

---

### Post by DanielWEWO on 2015-10-24
I checked in to the bug report. Hopefully this gets fixed.

---

### Post by lambdafox on 2015-10-27
> **QIII said:**
> ... [bug report]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888") and click on "... affects me too ..." to turn up the flame.

I was user #107 to join this bug report.  :mad:

---

### Post by lambdafox on 2015-10-28
[the count is up to 112 today]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1493888")

---

### Post by QIII on 2015-10-28
The fix was committed to wily-proposed some while ago.  There are people testing the fix.  When everyone is satisfied, the fix will be put in the Wily repo and the bug status changed to "Fix released".  Then you can install it.

---

### Post by mörgæs on 2015-10-29
Yes, a lot of work is going on, and people can install from Proposed as of today.

There is no need for more 'me too' statements.

---

### Post by lambdafox on 2015-11-01
> **mörgæs said:**
> Yes, a lot of work is going on, and people can install from Proposed as of today..

If you are not comfortable enabling the proposed repository, you can do this:

Download either the 32-bit or 64-bit versions of the .deb files from these three package pages on ubuntuupdates.org:

1. [fglrx-updates-core]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-updates-core")
2. [fglrx-updates]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-updates")
3. [fglrx-amdcccle-updates]("http://www.ubuntuupdates.org/package/core/wily/restricted/proposed/fglrx-amdcccle-updates")

Now you need to install those 3 deb files. 

I use Xubuntu. I just opened my file manager and right clicked, and installed using the Ubuntu Software Center application. If your file manager does not have a similar option, you may have to use dpkg.  If you use software center, it will complain the file is of bad quality. This simply means that it has not been through the normal review / release process.

In either case, install them in the order listed above.

xvba-va-driver is not yet in the Wiley repository; so, you will need to download the deb you need for it from [here]("https://launchpad.net/ubuntu/wily/+package/xvba-va-driver"). Now install this deb.

Next do this in your terminal:

```
sudo apt-get install libva-glx1 libva-egl1 vainfo
```

```
sudo amdconfig --adapter=all --initial
```

Reboot and Enjoy :D

Please be aware that this is a work around.  It just makes the fglrx drivers use the gcc 4.9 instead of Wiley's default of 5.0.  It does work for me, though.

Thanks, howefield & alison3 for your assistance.

---

### Post by vihochiamatiamici on 2015-11-13
Hi, lambafox. I tried to follow your guide but unsuccessfully. I'm using Ubuntu Gnome 15.10 whit the lastest kernel available on standard repo and fglrx driver installed from wily-proposed. I tried it on Ubuntu (Unity DE) and it worked fine for me. Now I'm not able to do the same on Gnome. I don't understand what actually changes.
I saw that** xvba-va-driver** is not yet in wiley's repo. Must I compile it from source? 
Does anyone have some suggestion?
Thanx

Paolo

---

### Post by mörgæs on 2015-11-20
-and now we have a Fix Released.

---

### Post by evan28 on 2015-11-23
Where may I find this fix? This iz my first ever ubuntu experience so any help would be appreciated.

---

### Post by Bashing-om on 2015-11-23
evan28; Hey ..

The fix has been released per AMD .. I have yet to be able to cross reference AMD's numbers to our repository .
What return do you now get :
```

apt-cache search fglrx

```

See if we have the driver availabale .

[INDENT][INDENT]maybe YES
[/INDENT][/INDENT]

---

### Post by evan28 on 2015-11-23
ok ill check and return tomorrow with an answer

---

### Post by evan28 on 2015-11-24
What should i do on this screen?

---

### Post by Bashing-om on 2015-11-24
evan28; Welp .

Post back the output:
```

apt-cache search fglrx

```
As I do not have 15.10 installed, I have no access to wily's repo. We compare what is avail to what was .. maybe the new driver is now available ? 
As a note and only as a means of last resort .. AMD advises the driver is available direct from them . The better course is to await completion of testing and the driver arrive in the repo .

[INDENT][INDENT]there is a way that seems right
[INDENT][INDENT][INDENT]but leads to a broke system
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

