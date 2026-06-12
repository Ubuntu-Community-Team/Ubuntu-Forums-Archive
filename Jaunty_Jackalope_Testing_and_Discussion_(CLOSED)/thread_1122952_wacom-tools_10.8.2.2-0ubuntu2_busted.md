---
title: "wacom-tools 1:0.8.2.2-0ubuntu2 busted"
date: 2009-04-11
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Roger E Critchlow Jr on 2009-04-11
I'm seeing the following symptoms on my thinkpad x200t:

wacomcpl - shows no devices present
xsetwacom list dev - shows no devices present

both of these showed stylus, eraser, cursor, and touch until the latest update.  The latest update did make xorg.conf auto configure the devices, so the drivers are still functioning, but without wacomcpl I can't recalibrate, and without xsetwacom I can't rotate the stylus coordinates when the laptop is rotated into tablet configuration.

Is anyone else seeing this?  Or is it an x200t specific problem?

-- rec --

---

### Post by Favux on 2009-04-11
Hi rec,

Is the Thinkpad X200t a usb tablet pc?

Gali98 is working on this, see post #77 here:  [http://ubuntuforums.org/showthread.php?t=1038949&page=8](http://ubuntuforums.org/showthread.php?t=1038949&page=8)

On the next post I mention the name of a new calibration utility they were developing.  Maybe it's in the repositories and maybe it will work with the new HAL/dBUS and .fdi file setup?

For rotation try Tom Jaeger's wacomrotate daemon, method 3 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)
You may have to use the gnome screen utility to actually rotate the screen.  But wacomrotate should get the stylus and eraser to follow.  It worked for a Thinkpad X61t user in Jaunty (at least during the alphas).

---

### Post by cywhale on 2009-04-11
+1
Acer Travelmate C110, pen is not usable with rotated screen in tablet mode (used xsetwacom and xrandr in rotate script with Ubuntu < Jaunty and Arch Linux until now). Wacomcpl and xsetwacon do not show devices. 
Wow, I did not have noticed that since installing Jaunty a few days ago - maybe there are other (new) ways to setup those devices (which are working fine in normal orientation and without any xorg.conf now) ?

---

### Post by cywhale on 2009-04-11
This bug seems to be already reported: [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358358]("https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/358358")

---

### Post by Roger E Critchlow Jr on 2009-04-11
@favux - thanks for jumping right in there.

I have no idea how to tell whether an internal wacom driver is usb or not.

There's no device reported by lsusb that's a wacom, there's nothing in /var/log/* that identifies the wacom as a usb device, the /dev/input/wacom is a link to /dev/ttyS0, but that doesn't mean that the wacom driver isn't a usb device which has cleverly disguised itself as a serial device so that someone at wacom wouldn't have to write some new code.

It sounds like we're just beginning to recognize the full extent of the problems, and that I'm not alone.

Has anyone filed a bug report?  

It's really neat that hal is picking up the devices without any need to hack on xorg.conf, but all of the screen rotation solutions that I've seen depend on xsetwacom to get the coordinates right, and the tablets are really, really hard to use when the stylus is reporting a coordinate system at 90 degrees to the one you're trying to use.

-- rec --

---

### Post by Favux on 2009-04-11
Hi rec,

It sounds like it's a serial tablet.  If you go to the link I gave you'll see bug reports have been filed.

If you go to the page before on that link you see where I made the announcement about Timo Aaltonen's patched 0.8.2-2 linuxwacom drivers.  The patches were from Fedora.  The idea was to finally get Wacom working with HAL/.fdi but it looks like there may be a problem.  See gali98's posts to the launchpad report near the bottom here:  [https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)
So the question is can we go back to xorg.conf?  And will that fix things?

---

### Post by Roger E Critchlow Jr on 2009-04-11
> **Favux said:**
> Hi rec,

For rotation try Tom Jaeger's wacomrotate daemon, method 3 here:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)
You may have to use the gnome screen utility to actually rotate the screen.  But wacomrotate should get the stylus and eraser to follow.  It worked for a Thinkpad X61t user in Jaunty (at least during the alphas).

The wacomrotate daemon calls xsetwacom to do the rotation, so it's broken too for the moment.

-- rec --

---

### Post by Favux on 2009-04-11
Thanks rec,

Good to know.  So the question is what is breaking xsetwacom.  It doesn't appear to be the new Xserver for Jaunty, 1.6.  I'm fairly sure that was already in place when the X61t user used it.

It may be the patched linuxwacom 0.8.2-2.  If so maybe compiling the new 0.8.3-2 development version would work after completely uninstalling 0.8.2-2 through Synaptic.  I think 0.8.3-2 is suppose to work in Jaunty.  It does work with kernel 2.6.28 according to the release notes.  The announcement for 0.8.3-1 said that 0.8.3-2 would work with Xserver 1.6 which 0.8.3-1 didn't yet.  But it isn't in the release notes for 0.8.3-2 that it does.  And of course you'd probably have to go back to xorg.conf.  But it seems they might have made some changes to xorg.conf along with introducing 1.6 just to complicate matters.  I'm kind of hoping gali98 has time to check that out.

---

### Post by Roger E Critchlow Jr on 2009-04-11
Well, there's the first problem:

wacom-tools-0.8.2.2/linuxwacom/src/util/wacomcfg.c:
#if WCM_XF86CONFIG
	/* read the config in for wacom devices which don't use the commnon identifier */
    #if WCM_XORG
	conf = readConfig ("/etc/X11/xorg.conf");
    #else
	conf = readConfig ("/etc/X11/XF86Config");
    #endif
#endif

There's nothing about wacom devices in that file anymore.

Hmm, looks like xinput can find the devices, so there must be an Xlib api that would work.

-- rec --

---

### Post by cywhale on 2009-04-11
Works fine, just tried the same idea (Favux') for the last 10 minutes :)

- downloaded [URL="http://linuxwacom.sourceforge.net/index.php/dl"]linuxwacom-0.8.3-2.tar.bz2
[/URL]- extracted and changed into linuxwacom directory
```
./configure --prefix=/usr
make
sudo make uninstall
sudo make install
```
- restored my old xorg.conf entries
- X restart

The stable 0.8.2-2 does not seem to work (compile error "error: xf86Version.h: No such file or directory") due to problems recognizing Xorg 1.6 ([there's mentioned a patch]("http://bbs.archlinux.org/viewtopic.php?id=65105") which is merged into 0.8.3-2) so I tried 0.8.3-2 which works fine.

Rotating works fine again.

---

### Post by Roger E Critchlow Jr on 2009-04-11
That's good news, I'll try it and report back.

Meantime, this:

   xsetwacom set "PnP Device (WACf008)" rotate cw

also works in 0.8.2.2 on my machine.  So if you install xinput, use it to find the true names of your stylus, eraser, and touch, (which probably won't match the one I used above) you can still rotate the screen.

-- rec --

---

### Post by Favux on 2009-04-11
Hi rec and cywhale,

Great work.  That looks like the problem.  A linuxwacom compile HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  may be of some assistance.

I'm curious.  If you search Synaptic with wacom do you see 0.8.2-2 wacom-tools in addition the the drivers?

Gali98 tried my suggestion (post #80) too and its working for him, post #81:
> Yes the old way works just fine (I'm using it now)
The current tutorial (if using 8.3-2) works perfect.
(as a note, make sure you DON'T have libhal1-dev installed, or it will compile with hal stuff which is what we don't want.)
Other than that everything is great.
[http://ubuntuforums.org/showthread.php?p=7056204#post7056204](http://ubuntuforums.org/showthread.php?p=7056204#post7056204)

---

### Post by Roger E Critchlow Jr on 2009-04-11
Sorry for the accidental smilie in the last post.

Here's a script which uses hal to figure out what wacom tablet inputs are enabled and what their names are in xinput.

[INDENT]#!/bin/sh

#
# translate the names used for wacom tablet inputs
# by xinput into the names used by the wacom driver
# using hal-find-by-property and hal-get-property
#

for udi in `hal-find-by-property --key input.x11_driver --string wacom`; do
	product="`hal-get-property --udi $udi --key info.product`"
	type="`hal-get-property --udi $udi --key input.x11_options.Type`"
	echo "product '$product' is type '$type'"
done
[/INDENT]

When I run it on my x200t I get:

[INDENT]product 'PnP Device (WACf008)' is type 'stylus'
product 'PnP Device (WACf008) touch' is type 'touch'
product 'PnP Device (WACf008) eraser' is type 'eraser'[/INDENT]

The product names are the ones that X is using to identify the devices, the type names are the ones that the wacom utilities are using.

So if we can hook this up to wacomcpl and xsetwacom then we should have a solution.

-- rec --

(Oops, almost posted more spurious smilies.)

---

### Post by Roger E Critchlow Jr on 2009-04-11
> **Favux said:**
> Hi rec and cywhale,

Great work.  That looks like the problem.  A linuxwacom compile HOW TO:  [http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)  may be of some assistance.

I'm curious.  If you search Synaptic with wacom do you see 0.8.2-2 wacom-tools in addition the the drivers?

Gali98 tried my suggestion (post #80) too and its working for him, post #81:

[http://ubuntuforums.org/showthread.php?p=7056204#post7056204](http://ubuntuforums.org/showthread.php?p=7056204#post7056204)

Yes, I get the same version of wacom-tools and xserver-xorg-xinput-wacom when I search for wacom in synaptic.

When I compiled and installed linuxwacom-0.8.3.3 I didn't at first notice that cywhale was reverting to his old xorg.conf, and everything was still broken.

I don't think putting configuration details into xorg.conf is a solution. The update was supposed to get rid of that, and I'm happy to get rid of it.  So I'd rather work out how to make the wacom-tools figure out how to get the right names and make wacomcpl and xsetwacom work with the new setup.

It seems like we may be fixing more than one thing in this thread.

-- rec --

---

### Post by Favux on 2009-04-11
Hi rec,

I have to say I'm following along with great interest.  I personally don't have any objection to xorg.conf but I appreciate where you're coming from.  At least we know the "old" method will work.

---

### Post by Roger E Critchlow Jr on 2009-04-12
> **Favux said:**
> Hi rec,

I have to say I'm following along with great interest.  I personally don't have any objection to xorg.conf but I appreciate where you're coming from.  At least we know the "old" method will work.

So I just tried compiling 0.8.2.3, installing it, reinstalling the xorg.conf which defined stylus, eraser, and touch, and restarting X.

It's a complete mess on my machine, I end up with the tablet input devices defined twice, once by xorg.conf and once by hal, and I can't tell whether rotation works or not because the stylus doesn't work at all.

So I'll say we have 3 classes of bugs in 0.8.2.2-0ubuntu2:

1) hal defines the devices, but they can't be calibrated or rotated;

2) hal defines the devices, but the definition is wrong in some essential way;

3) hal doesn't define the devices at all.

In cases 2) and 3) can probably be fixed by hacking on /usr/share/hal/fdi/policy/20thirdparty/10-wacom.fdi to get the right devices and properties passed into the x server.

Case 3) can also be fixed by reverting to an xorg.conf that defines the devices and using linuxwacom 0.8.2.3.  Cases 1) and 2) are not helped at all by reverting xorg.conf.

If you fix 2) and 3), they'll still be having a problem with 1), but maybe there's a way to fix 1) by hacking on the fdi file, too.

-- rec --

---

### Post by Favux on 2009-04-12
Hi rec,

When you compiled 0.8.3-2 did you make sure that libhal1-dev was not installed?  If it was present that's probably what's giving you the undesired HAL features.

Edit:  Actually it may be worse than you think from my perspective, gali98 on the launchpad bug report:
> The kernel module included with the current kernel just doesn't work (it gives error 113 as some people have already posted.) So I compiled the newest version of linux-wacom (8.3-2) and replaced JUST the module. I then had to edit the fdi file and replace it with my custom one
But I think I hit the brick wall. Now correct me if I'm wrong, but using this method, you can only pass options for one device (i.e. the first device you specify.) The others can only be added as devices - they can't be configured.
So he had to rewrite the .fdi to make touch the first device.  It was the only way he could calibrate touch.  The stylus's calibration was OK as a device, but it was not configurable.  This if correct, from my point of view, means there really isn't any advance over how things were in Intrepid.  We'll still need xorg.conf.  At least those of us who have touch.

---

### Post by gali98 on 2009-04-12
Right.. If you have libhal1-dev uninstalled, sudo make install doesn't install any hal related stuff. (You also have to purge xserver-xorg-input-wacom and wacom-tools, not just uninstall it. That may be your problem.
However even with that I am noticing that two devices are still created by hal named 
"Wacom ISDv4 93." I don't know how they got created, and they are empty devices.
Kory

---

### Post by Roger E Critchlow Jr on 2009-04-12
> **gali98 said:**
> Right.. If you have libhal1-dev uninstalled, sudo make install doesn't install any hal related stuff. (You also have to purge xserver-xorg-input-wacom and wacom-tools, not just uninstall it. That may be your problem.
However even with that I am noticing that two devices are still created by hal named 
"Wacom ISDv4 93." I don't know how they got created, and they are empty devices.
Kory

Arghh.  I sure wish I had git to manage branches in my system configuration.  So, to actually give linuxwacom-0.8.2.3 a fair shake, I need to uninstall libhal-dev and purge all the other wacom packages I would normally use?

But there _are_ multiple problems with the hal based configuration: 

  can't rotate using the normal device names, 
  can't calibrate using wacomcpl,
  can't specify fixed calibration in an fdi file

and maybe others, but no one's claimed them yet.

Can you append the calibrations, and other customizations, to the hal installed configure with hal-set-property?  Or do the properties need to be there at the initial construction to be effective?

-- rec --

---

### Post by schmolch on 2009-04-12
I cant get this working.

Since about 2 weeks X is broken on my 2 jaunty-installs on my Tablet-PCs.
When i use the linuxwacom pkg from jaunty i am forced to remove the wacom stuff from my xorg.conf because otherwise X will only show some colored lines and restart forever.
Without the wacom-stuff i cant rotate the screen though cause xsetwacom needs the device-name from xorg.conf
With the latest dev-pkg of linuxwacom X never works regardless if i have the wacom-config on my xorg-conf or not. The only way to get it working again is removing linuxwacom completely.

---

### Post by Roger E Critchlow Jr on 2009-04-12
> **Roger E Critchlow Jr said:**
> 
Can you append the calibrations, and other customizations, to the hal installed configure with hal-set-property?  Or do the properties need to be there at the initial construction to be effective?

Ah, the answer is yes and yes.  If you alter the hal properties while the Xserver is running, it doesn't notice.  But the altered properties will be there when the Xserver restarts and it will see them then.

So, if we write /etc/init.d/wacom and link it as /etc/rc{2,3,4,5}.d/S27wacom, after hal and before gdm, then we can modify the hal properties before the xserver sees them for the first time.

[INDENT]# find any wacom devices
for udi in `hal-find-by-property --key input.x11_driver --string wacom`
do
  type=`hal-get-property --udi $udi --key input.x11_options.Type`
  # rewrite the names that the Xserver will use
  hal-set-property --udi $udi --key info.product --string $type
  case $type in
  stylus|eraser)
   # map stylus button 2 to mouse button 3
   hal-set-property --udi $udi --key input.x11_options.Button2 --string 3
  ;;
  esac
done
[/INDENT]
So that works for renaming the input devices back to what wacomcpl and xsetwacom expect them to be, so rotation and interactive calibration work, and it also enables context menus off the stylus button.

And Kory should be able to stick his calibrations in there, too.

Anything that used to be in xorg.conf can be inserted into the hal properties this way.  And it can all go away when the fdi files are working correctly.

-- rec --

---

### Post by Favux on 2009-04-12
Hi rec,

Nice job.  You **_need_** to post this to the bug report so it can be verified and hopefully incorporated.

[https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340](https://bugs.launchpad.net/ubuntu/+source/wacom-tools/+bug/355340)

It isn't just a bug report, it's where Timo Aaltonen wanted feedback to his modified 0.8.2-2 (patched to work with HAL).

Edit:  Saw your report.  It should help move things along.  Thank you.

---

### Post by Favux on 2009-04-13
Hi rec,

I have a question about linking the script after I install it in /etc/init.d/wacom.  Do I do?:
```
sudo update-rc.d wacom start 27 2 3 4 5 .
```
And is there a problem if I also link the non-user run levels like 1 and 6?

---

### Post by gali98 on 2009-04-13
Wow!
 Rec you are amazing... I'll try this when I get home today and tell you what I find.
So basically once this script runs, I should be able to run my .xinitrc file (where wacomcpl stores all its settings) and it should calibrate and it should work just like normal right? 
If I understand it right, if xsetwacom is able to get to the device, it shouldn't matter whether the device is a hal sub-device or not.
This is making me excited! I'm just worried that even if we do get it all worked out, it won't make it in time for jaunty :\
Thanks!
Kory

---

### Post by gali98 on 2009-04-13
It Works!!!

Right now I'm just working out the kinks. Two sets of devices are still being created (and it has absolutely nothing to do with the rules file. I removed every wacom rules file and multiple sets are still being created. )
Maybe it has something to do with there being two events? (one for stylus/eraser and one for touch)
I can calibrate with wacomcpl and all the buttons can be configured.
However for some reason touch will not calibrate. I can do it with xsetwacom, but when I try to do it graphically, the clicks do not register with the boxes.. No idea about that.
At this point I have to check out for a few days. I'll be a fly on the wall, but I've got a lot of school work I've got to do. Thanks guys!
Kory

---

### Post by Favux on 2009-04-13
Outstanding!

My guess to explain the duplicates is that the dBUS callout is seeing both of our input paths. Since our Wacom digitizer is on one usb path and the touch panel on another.  Using the wacom strings query it is ending up with stylus, eraser, and touch on each path. Hence wondering if for our tablet pc we should use two .fdi files. I'm not sure how that would interfere with touch calibration after using rec's script.

---

### Post by gali98 on 2009-04-13
Ugh!! I cannot track down where those two empty devices (Wacom ISDv4 93) are being created!
I have gone through every single stinking fdi file and can't find anything! The tablet Pc fdi file I completely deleted and it didn't make a difference. Is there some kind of hal log file we can look at?
Kory

---

### Post by Roger E Critchlow Jr on 2009-04-13
> **Favux said:**
> Hi rec,

I have a question about linking the script after I install it in /etc/init.d/wacom.  Do I do?:
```
sudo update-rc.d wacom start 27 2 3 4 5 .
```And is there a problem if I also link the non-user run levels like 1 and 6?

I never found the update-rc.d command, I just linked by hand.  From the man page, you could also do:```
sudo update-rc.d wacom defaults 27
```.

Should be no problem with linking to other run-levels, as long as your script doesn't have cumulative changes.  The script I wrote has the same result no matter how many times you run it.

-- rec --

---

### Post by Favux on 2009-04-13
Hi again rec,

Thank you, that was helpful.

---

### Post by schmolch on 2009-04-14
Wow that works, thanks alot to everyone.

---

### Post by gali98 on 2009-04-18
I got everything working on My USB Tablet PC! 
What's more, with the way I found, it gets rid of all the extraneous devices. Calibration, Rotation, and wacomcpl work great!
Thanks so much to Rec and Favux (and Timo)!
See Posts 102 and 104 for all the info, and a small (well not so small) how-to on this page:
[http://ubuntuforums.org/showthread.php?t=1038949&page=11](http://ubuntuforums.org/showthread.php?t=1038949&page=11)
Thanks!
Kory

---

