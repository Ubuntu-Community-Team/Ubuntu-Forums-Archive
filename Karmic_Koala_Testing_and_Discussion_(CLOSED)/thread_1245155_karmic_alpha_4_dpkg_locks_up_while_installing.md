---
title: "karmic alpha 4: dpkg locks up while installing"
date: 2009-08-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gward on 2009-08-20
I downloaded Xubuntu 9.10 (karmic) alpha 4 last night and tried to install on an empty partition.  This is my first exposure to either Xubuntu or karmic, so I'm not sure where the problem is.  I think ultimately there is an installer issue, so I'm reporting it here.

Installation chugged along for a while, but eventually got stuck for several hours.  I dug around with "ps" and "strace" a bit and figured out that this command:

  dpkg --root=/target --status-fd=xx --configure ...long list of packages...

was blocked reading from stdin.  So I killed that dpkg process.  The installer showed an error message, then chugged along for a while more and got stuck again doing the same thing.  So I killed it again.  Eventually it finished with more errors.

(Oh yeah: this is all from memory of what I did an hour ago, so the details might be wrong.  Please let me know if you need more precision and I'll try to replicate the problem.)

Before rebooting, I tried running the command manually (without --status-fd=xx), and dpkg complained about /etc/pulseaudio-client.conf, saying I had deleted it and the package wanted to provide it.  Reactions: 1) that's odd; it's a brand-new installation, so who has been mucking about in /etc? not me!  2) this probably explains why dpkg --configure was blocked on stdin.

In the end, I failed to dpkg --configure various packages, notably libc.  That worried me.  But I figured what the heck, go ahead and reboot anyways and see if it works.

It does not.  The system gets as far as asking me to login, which I do successfully.  I get a shell prompt in the upper-left (no windows or window manager apparent -- is this a Xubuntu thing?) and a stopwatch mouse cursor.  And that's it.  The system has been stuck there for ~60 minutes.

Questions:

  * is this installer in karmic alpha 4 broken, or is this just a 
    Xubuntu thing?  I.e. should I avoid alpha 4, or just try the 
    standard installer instead of Xubuntu?

  * is the installation freeze and failure to configure libc likely
    responsible for the wedged login process?  or are they different?

Thanks!

Greg

---

### Post by slakkie on 2009-08-20
I had installation freezes like this with livecd installers. Perhaps an error on the CD?

You could try installing it with the net install:

[http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/karmic/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by jfernyhough on 2009-08-20
Sounds to me like an installer bug. So yes, either use the netinstall or grab a daily LiveCD. e.g. [http://ftp.heanet.ie/mirrors/ubuntu-cdimage/xubuntu/daily-live/current/](http://ftp.heanet.ie/mirrors/ubuntu-cdimage/xubuntu/daily-live/current/)

---

