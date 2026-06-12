---
title: "unable to add pmscenery for iPhone support"
date: 2011-11-14
forum: Installation &amp; Upgrades
---

### Post by eltonw on 2011-11-14
While Oneiric recognises my IPhone 3GS, it refuses to mount the device. It would pop up this error message:

[B]Unable to mount {username}’s iPhone
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)[/B]

To correct this, the solution is to add **pmscenery**.
I have managed to add the repository for **pmscenery** to Oneiric Ocelot, as per instructions HERE:
[https://launchpad.net/~pmcenery/+archive/ppa/?field.series_filter=karmic]("https://launchpad.net/%7Epmcenery/+archive/ppa/?field.series_filter=karmic"). Nevertheless, I still can't install the package. 

This is the *error message* shown in the console session:

[COLOR=Red]W: Failed to fetch [http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pmcenery/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
[/COLOR]
What am I doing wrong?

---

### Post by M1NDF1R3 on 2012-01-15
You havent done anything wrong, its as simple as this... there is no PPA support for the IPhone on 11.10 oneiric.

I have been searching this issue for months, literally! best i can get so far is installing clementine music player which will at least give you the ability to transfer and delete music to and from the phone, but the ability to browse the phones files to get access to photo's is not available at the moment. Or if it is whoever has figured out how to do it is keeping it to them selves.

---

### Post by eltonw on 2012-01-16
I have installed a different distro _***based on*** ubuntu _oneiric. 

Now, when I connect the iPhone (running IOS 5.0.1, I am able to manage my music and pictures. Of course, [COLOR="Navy"][FONT="Tahoma"]there is no support to sync address books or the calendar[/FONT][/COLOR], but considering that you are dealing with Apple, this is not going be easy for the linux community to get that support for the iPhone. 
                  
                 ... even 'impossible', one might say.

---

