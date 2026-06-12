---
title: "Help!  External modem installation?"
date: 2005-04-30
forum: Installation &amp; Upgrades
---

### Post by bigkahuna on 2005-04-30
Hi,

I just bought an external 56k modem -just- to use with my fresh install of Ubuntu Haory and I can't figure out how to install it.  I searched the archives and didn't find a thing!

It's a Best Data model 56SX-2 56k serial external modem and it's connected to serial port #1.  I'm connecting through Windoze XP right now.

I read many reviews on this modem and it's supposed to work perfectly with Linux... is there and easy "How To" anywhere?  Help?!?!

Paul

---

### Post by az on 2005-04-30
Use the networking tool in System - administration- networking.  Configure your modem conection.  Have it autodetect your modem.

---

### Post by bigkahuna on 2005-04-30
Thanks Azz,

That helps, but something still isn't working right.  I read the Gnome help pages and I think they're for an older version of Gnome (at least they didn't help much).

Ok, I went to System -> Administration -> Networking and I set up a new connection which I named "Modem".  You have to click on the "this device is already configured" box in order to get it to "auto detect" which I did, then I entered all the info for my dial up host.  Then I "activated" the modem connection and heard the modem dial and connect.  In this same configuration panel I also selected the "use modem as default device for the internet" box, which seems right.

So I should be connected to the internet, right?  So I next launched Firefox and tried to go to a website and I got "address not found".

My questions:

1.  What am I doing wrong?
2.  I'd like to configure the system so that if I launch Firefox (or any other internet application, like Thunderbird) it automatically "activates" my modem connection.  How do I do this?
3.  Shouldn't there be a How To on this somewhere?  Seems like an awefully common thing to connect a modem?  I searched and searched and didn't find anything.

Thanks,

Paul

---

### Post by jkndrkn on 2005-05-27
I have the same problem bigkahuna mentioned above..
Any takers?

---

### Post by bigkahuna on 2005-05-27
I never got my modem to work with Ubuntu, so I gave up and installed Kanotix (Debian Sid) and now everything works perfectly.

One thing you might try (and I wish I knew this before) is a small application called "wvdial".  It might already be installed with Ubuntu or may be in the Ubuntu repository.  At any rate, get wvdial and google for instructions on how to use it.  Wvdial is a command line utility that does an -excellent- job at detecting and autoconfiguring external modems.  GnomePPP (the standard Gnome dialer) is just a frontend for wvdial.  If wvdial doesn't work, I doubt if anything will...

Hope this helps.

---

### Post by jkndrkn on 2005-05-27
Yes, I started experimenting with wvdial and gnome-ppp. I will let you know how things turn out.

Thanks for the pointers.

---

### Post by Zonkle on 2005-05-28
[QUOTE=bigkahuna]I never got my modem to work with Ubuntu, so I gave up and installed Kanotix (Debian Sid) and now everything works perfectly.

One thing you might try (and I wish I knew this before) is a small application called "wvdial".  It might already be installed with Ubuntu or may be in the Ubuntu repository.  At any rate, get wvdial and google for instructions on how to use it.  Wvdial is a command line utility that does an -excellent- job at detecting and autoconfiguring external modems.  GnomePPP (the standard Gnome dialer) is just a frontend for wvdial.  If wvdial doesn't work, I doubt if anything will...

Hope this helps.[/QUOTE]
 Ok what about Internal Modems ?

Till now I can't make it work :(

Any body can help?

My modem is AC 97 - PCTel 56 - HSPR 56 MR .

Thanks.

---

