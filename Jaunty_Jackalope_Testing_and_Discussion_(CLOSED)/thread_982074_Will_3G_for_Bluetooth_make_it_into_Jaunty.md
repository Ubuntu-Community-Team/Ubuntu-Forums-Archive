---
title: "Will 3G for Bluetooth make it into Jaunty?"
date: 2008-11-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Starks on 2008-11-14
I was extremely disappointed that this feature did not make the cut for NM 0.7 and by extension, Intrepid.

---

### Post by PmDematagoda on 2008-11-14
If the next version of Network Manager doesn't get released in time for Jaunty, then no. In fact, I don't think work on Network Manager 0.8(or whatever the next release will be) has begun.

---

### Post by plun on 2008-11-15
From Dan Williams blog:

[http://blogs.gnome.org/dcbw/](http://blogs.gnome.org/dcbw/)

> But what’s not on the list?

Bluetooth: a bunch of work, but will be a major driver of 0.7.1 or 0.7.5


I am using wvdial until its ready.
[https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing#Probing](https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing#Probing) bluetooth modems

---

### Post by Starks on 2008-11-17
> **plun said:**
> From Dan Williams blog:

[http://blogs.gnome.org/dcbw/](http://blogs.gnome.org/dcbw/)




**I am using wvdial until its ready.**
[https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing#Probing](https://wiki.kubuntu.org/NetworkManager/Hardware/3G/Probing#Probing) bluetooth modems

same here. however, setting up a cdma modem is rather tricky.

---

### Post by scaine on 2008-11-17
You might want to try [BlueMan]("http://blueman.tuxfamily.org/").  You have to [set up its repos]("http://blueman.tuxfamily.org/index.php?option=com_content&view=article&id=51&Itemid=56") and it will un-install Bluez, but otherwise it's very impressive.  There's even Network Manager 0.7 hooks - you query the phone, find it's DUN entry, bind to it, then tick the box to bind the DUN to Network Manager so that it pops up as a wireless network.

The security on my Blackberry has prevented me testing beyond this (when I try connecting, it fails and drops me back to my WIFI connection), but it certainly looks like they've covered everything you need assuming that you have a compatible phone.

The most impressive thing about Blueman is that you won't ever need to use a command line to transfer files to/from your phone, or set up an internet connection through it.  Well... at least I didn't!  :-)

Although I notice that their forums talk about [incompatibilities with Intrepid]("http://blueman.tuxfamily.org/forum/viewtopic.php?f=4&t=97&sid=ff76919ca919a5ee65a4cfe5ee977736") (I didn't have any issues, beyond my phone's issues with dial-up).

---

### Post by scaine on 2008-11-28
Update :
I used the latest 0.6 Blueman using this PPA : [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main, on the latest Intrepid.

I gave up on my blackberry and tested with a Nokia 6233.  Worked perfectly.  You run Blueman, pair the device using the gui, right-click on the phone entry and choose "New Serial Port", then choose the "Dial-Up Networking" service that appears from the many available services that this phone supports.  Then choose your newly created rfcomm0 entry and tick the box for "This is a GSM/GPRS/EDGE/3G Dial Up Connection" which pops an entry into Network Manager 0.7.

Then click on your NM applet and there will be an entry for "Mobile Network" saying "Configure".  When you click on that, it will ask you the usual questions - which country are you in and which provider do you use.

After that, you can safely disabled your WIFI connection and click on that entry from the NM0.7 applet.  You'll see connection notifications from Blueman as the bluetooth connection is dialled, and you should be connected almost instantly.

Web browsing is a little strange because you'll often notice a lot of NAT addresses flashing past in your firefox status bar instead of the "real" public IP of the sites you're browsing, but otherwise it works very quickly and smoothly!

---

### Post by plun on 2008-11-28
Magic.....:)   Goodbye wvdial, i will not miss you.

A pics showing how it works

[[img]http://ubuntu-pics.de/thumb/6478/screenshot_80Yotm.png[/img]](http://ubuntu-pics.de/bild/6478/screenshot_80Yotm.png)


If blueman now could maybe unite with NM this will be great....

---

### Post by Starks on 2008-11-28
CDMA 3G still doesn't work outside of wvdial.

---

### Post by plun on 2008-11-28
> **Starks said:**
> CDMA 3G still doesn't work outside of wvdial.

Works just fine for me on my cell phone, S-E K610 and a 3G connection.

Also tested my speed against a reference server and its exactly what
I pays for.

---

### Post by Eclipse. on 2008-11-28
> **plun said:**
> 

[[IMG]http://ubuntu-pics.de/thumb/6478/screenshot_80Yotm.png[/IMG]]("http://ubuntu-pics.de/bild/6478/screenshot_80Yotm.png")




Theme details? :)

---

### Post by plun on 2008-11-29
> **Eclipse. said:**
> Theme details? :)
 OT warning....   Wallpaper from [Vlad]("http://www.vladstudio.com/home/"), Theme from [Cimi]("http://www.cimitan.com/murrine/node/125"), carbon
and Emerald theme is Blackline
OT end...

Blueman works great after some more tests   ....:)

---

### Post by rykel on 2009-04-12
Hi all,

Hope I am not replicating any threads here...

But I am using Blueman (from ppa) with Jaunty, and while it can browse my Nokia 6121 Classic phone just fine, Network Manager does NOT seem to detect any mobile broadband connectivity...

Just wanted to put this issue out to the open in case someone else might need the info.

I hope this gets sorted out soon!   : )

---

