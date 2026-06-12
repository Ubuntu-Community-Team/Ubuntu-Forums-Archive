---
title: "gnome+kde=hell"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tagbre on 2008-10-25
There are 2 issues that actually started with hardy and I hoped they'd be solved in this release, but they aren't.

I have both Gnome and KDE installed

1. I can't have different default apps for each environment (for example, make Banshee default mp3 player in Gnome and Amarok default mp3 player in KDE.

2. Gnome and KDE now share autostart apps, so, for example, 'Knetworkmanager' starts with gnome, and 'Networkmanager applet' (gtk) starts with KDE.

Any ideas on how to solve this?

---

### Post by tagbre on 2008-10-28
bump

---

### Post by Daimoneze on 2008-10-28
In my experience this is **the** issue of having both. It doesn't occur to me that this is something that will ever be "fixed" as it's not really broken. Generally people will use one or the other.

---

### Post by tagbre on 2008-10-28
Well, this was not an issue untill Hardy (I've been using every Ubuntu release since Warty).

Plus, i personally think that this is a limitation to the user: I am limited to use **one** desktop environment, because if I want to use more than one, I'll have these inconveniences.
I think one of the strengths of free software is the fact that the user can choose what he wants to use, and I choose **both** desktop environments. 
Just my humble opinion...

---

### Post by klamari on 2008-10-28
I have Ubuntu and Kubuntu (Gnome and KDE) on separate partitions, one partition as data-partition, so I can choose which I want to use on boot. 
Serves well to me...didn't want to have all the programms of both showing up in the menu anymore, so I decided to separate them...

Greetings 

martin

---

### Post by supernovus on 2008-10-29
> **tagbre said:**
> There are 2 issues that actually started with hardy and I hoped they'd be solved in this release, but they aren't.

I have both Gnome and KDE installed

1. I can't have different default apps for each environment (for example, make Banshee default mp3 player in Gnome and Amarok default mp3 player in KDE.

2. Gnome and KDE now share autostart apps, so, for example, 'Knetworkmanager' starts with gnome, and 'Networkmanager applet' (gtk) starts with KDE.

Any ideas on how to solve this?

The two "bugs" you mentioned are actually "features". However, those features may not have been implemented as optimally as possible by Ubuntu.

1. The default apps are specified by the Shared MIME Database specification. All desktop environments should be using this database. However, the idea is that typically a single user will be using a specific desktop environment and set of applications the most. Different users can have different sets of applications of course. However they will be shared betweeen all desktop environments that implement the specification. This is not an Ubuntu specific issue, but something we just have to get used to as desktop environments work towards better compatibility.  We could suggest to FreeDesktop.org to add the ability to give preference to apps depending on desktop environment. Then both Gnome and KDE would have to update to use the new standard. For now, I'm just living with how it works now.

2. This IS an Ubuntu issue. In the case of NetworkManager versus KNetworkManager, they should not be both starting. The Autostart specification is also a FD.O standard, and is implemented by both Gnome and KDE. This is good. The standard has a method to stop certain applications from autostarting in certain desktop environments. However, it appears that the Ubuntu profiles are not implementing those features:

[http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-0.5.html)

Since both Gnome and XFCE use NetworkManager, the use of OnlyShowIn is not that good, but NetworkManager should have a NotShowIn set on KDE, and KNetworkManager should have a NotShowIn set to Gnome and XFCE. This is something that should be reported as a bug (if it isn't already, I haven't checked yet.)

So there you have it. Nothing to be done about issue #1, as it's acting properly. But issue #2 is not acting properly, and should be fixed using the NotShowIn keys.

Hope this has helped a little.

---

### Post by tagbre on 2008-10-30
Thanks for the info supernovus. I guess all I can do is have a different user for each environment. That way I can have apps associated the way I want.

---

