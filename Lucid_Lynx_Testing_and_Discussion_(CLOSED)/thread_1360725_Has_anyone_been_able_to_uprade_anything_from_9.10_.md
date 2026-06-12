---
title: "Has anyone been able to uprade anything from 9.10 to 10.04 recently"
date: 2009-12-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ranch hand on 2009-12-21
I have tried for the last 3 or maybe4 days and fail every time with a BUNCH of dbus config errors.

My latest try was a minimal install.  Just won't do it.

---

### Post by dino99 on 2009-12-21
i've upgraded since the beginning: got the dbus warning several times last week but now it's ok except troubles with dkms/nvidia/kernel .33

hard to boot, trying with nomodeset and/or nouveau.modeset=0 but no success

---

### Post by buzzmandt on 2009-12-21
2 days ago on laptop, karmic to lucid, got an error during upgrade.  ran upgrade again without rebooting and all went fine.  my son is playing on it now.  kde is still a little bit hindered and running gnome rtm.  otherwise it's doing fine

---

### Post by ranch hand on 2009-12-21
I do not know what the problem is.

There is  /var/run/dbus/system-bus-socket that exists in 9.10 but not 10.04 (none of mine have it) that stops dbus from getting configured every time.

This balloons from there and then the "installation stopped because of too many errors" comes up.

I figures a minimal install would be the way to go and just upgrade it before adding anything to it.  Didn't work.

---

### Post by buzzmandt on 2009-12-21
trying it now on my desktop karmic to lucid, nvidia video. will let you know how it goes

---

### Post by ranch hand on 2009-12-21
I just thought you might be interested in this.  It is very like the lists that normal 9.10 installs for Ubuntu so the problem is real basic;
> 
Errors were encountered while processing:
 dbus
 gconf2-common
 hal
 system-tools-backends
 gnome-control-center
 consolekit
 liboobs-1-4
 libgnomevfs2-0
 dasher
 evolution-plugins
 dbus-x11
 gnome-accessibility
 evolution
 gnome-screensaver
 gnome-system-tools
 gconf2
 swfdec-gnome
 libgnome2-0
 gnibbles
 gnome-applets
 totem-common
 hamster-applet
 gstreamer0.10-plugins-good
 dasher-data
 ekiga
 avahi-daemon
 pulseaudio
 gnome-session-bin
 swell-foop
 aisleriot
 policykit-1
 gnotski
 gconf-defaults-service
 gnome-power-manager
 libbonoboui2-0
 python-gnome2
 seahorse-plugins
 empathy
 pulseaudio-module-x11
 gdm
 glines
 libgstfarsight0.10-0
 lightsoff
 eog
 gnome-system-monitor
 gconf-editor
 gnome-settings-daemon
 gtali
 python-gnomeapplet
 capplets-data
 seahorse
Processing was halted because there were too many errors.

This is taken after trying to install the first dependency not auto installed for the installation of the gnome desktop (package=gnome) I forget what that package is.

dbus was on there from the original attempt to upgrade as were about1/3 of the list.

---

### Post by buzzmandt on 2009-12-21
ok, so far same thing that happened on laptop, upgrade progressed to brasero and ended with error, ran sudo apt-get dist-upgrade -f in order to fix and continue.  will update how it goes from here

---

### Post by ranch hand on 2009-12-21
I hope it works for you.  I tried the "-f" route and it didn't go any better.  It would download more stuff but just couldn't get enough to configure to go on.

---

### Post by uBeer on 2009-12-21
I just updated my laptop to 10.04. I had xorg-edgers enabled and somehow it removed xorg-server-ati and radeon (and I wasn't paying attention ;)) but after I installed those packages again I got it pretty much running. Though no wireless yet and my trackpad doesn't work yet, but I'm gonna fix m now.

Compiz running well and VT switching with no delay and in native resolution: awesome!

---

### Post by autark on 2009-12-21
I upgraded my laptop today, without running into your kind of trouble. Your post makes wonder whether I did full a upgrade or not. 

I simply changed all instances of "karmic" to "lucid" in /etc/apt/sources.list, upgraded apt and ran "apt-get update" and "apt-get upgrade". Of course I had to fix some broken dependencies, but basically, that's it.  

I had one piece of trouble though, a Python syntax error when configuring app-install-data, but that's all. And, the nvidia drivers are a mess, but that's a known problem.

Am I missing some step in the process?

---

### Post by ranch hand on 2009-12-21
> **autark said:**
> I upgraded my laptop today, without running into your kind of trouble. Your post makes wonder whether I did full a upgrade or not. 

I simply changed all instances of "karmic" to "lucid" in /etc/apt/sources.list, upgraded apt and ran "apt-get update" and "apt-get upgrade". Of course I had to fix some broken dependencies, but basically, that's it.  

I had one piece of trouble though, a Python syntax error when configuring app-install-data, but that's all. And, the nvidia drivers are a mess, but that's a known problem.

Am I missing some step in the process?
I suspect that you are still running on the 9.10 kernel.  The plain "upgrade" should have held the kernel back.

You would need to run "dist-upgrade to get that.

---

### Post by autark on 2009-12-21
> **ranch hand said:**
> I suspect that you are still running on the 9.10 kernel.  The plain &quot;upgrade&quot; should have held the kernel back.

You would need to run &quot;dist-upgrade to get that.

No, I got 2.6.32-9-generic, after some fiddling. 

By the way, the first thing I see on booting: a segmentation fault. Where do I look to see what that is about?

---

### Post by ranch hand on 2009-12-21
Run a search on this thread for that.  There are a few threads here about that.  See "search this thread" at top of page.  I would use "segmentation".

---

### Post by ranch hand on 2009-12-21
I have an upgrade from minimal.  Just started with "-f".

Trying to get "gnome desktop environment" in and updated with things I like and the restricted extras.  So far so good.

I am doing this by chroot so that boinc can run here on Lounge Lizard.

Have to get out of here and see if it really is all there.

I am excited.

---

### Post by ranch hand on 2009-12-21
Well, I am back.  Won't boot.  Won.t boot to recovery.  I will fool with it a few days and see if some updates will help.

---

### Post by buzzmandt on 2009-12-21
Upgrade did ok for me as long as i don't try to install nvidia drivers.  tried repo drivers and drivers from nvidia website.  after trying nvidia drivers driver nv wouldn't work either.  i just installed karmic again and upgraded to lucid.  leaving nv driver default for now.  will try again later.

Other than that everything went fine

---

### Post by ranch hand on 2009-12-21
Well my upgrade worked.

I have never done the minimal thing before, or the gnome desktop either, so I probably need to
work on it.

I got 2 brief warnings before that black screen on the first boot attempt.  There is a problem with both x and gdm.

There was a short blast of stuff when I tried recovery, couldn't read any of it, and then just the black screen.

Oh well.

I will try something I understand and try this again.  Didn't work before (I have updated versions of 10.04 working - I am on one).  But maybe things have changed.

---

### Post by phillw on 2009-12-21
On A1, I'm not sure if the devs are really concentrating on 9.x --> 10.x upgrades

IMHO, doing so at this stage would create more issues than a clean 10.04 A1 in its own area.

Getting LL happy & running is the #1 task, until LL is at about the beta stage, the devs should not be worrying about "updating"

just my $0.02

Phill.

---

### Post by ranch hand on 2009-12-21
phillw
I think that you are right.  They also have to get 8.04 to upgrade to the bugger.

That should be FUN.

---

### Post by garvinrick4 on 2009-12-21
This worked for me just fine.


 sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by Michalxo on 2009-12-21
I upgraded from karmic (alpha3++) with full updates to lucid using renaming source.list.

I had problems with nvidia drivers which always tried to remove xorg and xserver and vice versa. I managed to repair it so it worked, but I went back to fresh karmic installation.

---

