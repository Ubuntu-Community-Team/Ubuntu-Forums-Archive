---
title: "Karmic upgrade removed asterisk &amp; broke asterisk-gui"
date: 2009-12-13
forum: Installation &amp; Upgrades
---

### Post by gadg3ts on 2009-12-13
Among the number of things that seems to have broken on my home server after upgrading 9.04 to 9.10 is this:
I discovered that asterisk had been removed and when I reinstalled it, the gui looks to have moved, without any indication of where it should now be...

Because asterisk-gui isn't an ubuntu package, previously I grabbed it from subversion and made it work as detailed here:
[http://www.asteriskguru.com/board/asterisk-gui-on-ubuntu-working-vt3810.html?highlight=](http://www.asteriskguru.com/board/asterisk-gui-on-ubuntu-working-vt3810.html?highlight=)

Yet for 9.10. that doesn't do it. Asterisk config files are the same.

So what I need to know, is where is asterisk 1:1.6.2.0~rc2-0ubuntu1.1 expecting static-http to be served from, as it doesn't appear to be either of:
/var/lib/asterisk/static-http 
/usr/share/asterisk/static-http

Any pointers?

Thanks,
Sean.

---

### Post by gadg3ts on 2010-02-07
Well...
Now that I've moved the fxs card to a different machine I thought I'd try again.
According to the ubuntu asterisk sources, the static data is installed into:
/var/lib/asterisk/static-http
Which is, helpfully enough, where the 'make install' from the asterisk-gui svn co puts it.

Now what I get from:
[http://gateway:8088/asterisk/static/](http://gateway:8088/asterisk/static/)
is a 403 Access Denied, so there is *something* being served, from somewhere...
But what, or where, is escaping me.
static-http is -R owned by asterisk:asterisk

/etc/asterisk/http.conf contains:
[general]
enabled=yes
enablestatic=yes
prefix=asterisk
redirect=/ /asterisk/static/config/cfgbasic.html
bindaddr=0.0.0.0
bindport=8088

I've tried strace to find out what isn't being served, but that's not been much help so far...

Anyone?

---

### Post by gadg3ts on 2010-02-07
Ok. In a roundabout way I've fixed access to the gui.

Add this ppa to get an actual deb for asterisk-gui:
[https://launchpad.net/~dajhorn/+archive/pkg-voip?field.series_filter=karmic](https://launchpad.net/~dajhorn/+archive/pkg-voip?field.series_filter=karmic)
(aptitude install asterisk-gui)
Whatever that does differently from installing from svn worked.

Then, there'll probably be an issue with an endless loop trying to log in, on "Verifying Dialplan Contexts needed for GUI" 
Steps taken:
chown -R asterisk:asterisk /etc/asterisk/ /etc/dahdi/

Then to stop asterisk itself complaining about its own generated /etc/dahdi/system.conf:
cd /etc/dahdi && cp system.conf system.conf.tmp && grep -v "^#" system.conf.tmp > system.conf

Hopefully that'll be of use to someone else!

Which now gets me back to the stage I was at before upgrading to karmic, which is getting Asterisk + Siemens a580ip/A58H to do more than forward voicemail to email...

---

