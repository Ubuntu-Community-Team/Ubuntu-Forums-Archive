---
title: "New Notification System in Jaunty!"
date: 2009-02-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ghindo on 2009-02-21
Mark Shuttleworth announced today that [a new notification system will be implemented in Jaunty]("http://www.markshuttleworth.com/archives/265").> Thanks to the concerted efforts of Martin Pitt, Sebastien Bacher and several others, notify-osd and several related components landed in Jaunty last week. Thanks very much to all involved! And thanks to David Barth, Mirco Muller and Ted Gould who lead the development of notify-osd and the related messaging indicator.

Notify-OSD handles both application notifications and keyboard special keys like brightness and volume

MPT has posted an overview of the conceptual framework for “attention management” at [https://wiki.ubuntu.com/NotificationDesignGuidelines](https://wiki.ubuntu.com/NotificationDesignGuidelines), which puts ephemeral notification into context as just one of several distinct tools that applications can use when they don’t have the focus but need to make users aware of something. That’s a draft, and when it’s at 1.0 we’ll move it to a new site which will host design patterns on Canonical.com.

There is also a detailed specification for our implementation of the notification display agent, notify-osd, which can be found at [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD) and which defines not only the expected behaviour of notify-osd but also all of the consequential updates we need to make across the packages in main an universe to ensure that those applications use notification and other techniques consistently.

There are at least 35 apps that need tweaking, and there may well be others! If you find an app that isn’t using notifications elegantly, please add it to the notification design guidelines page, and if you file a bug on the package, please tag it “notifications” so we can track these issues in a single consistent way.

Together with notify-osd, we’ve uploaded a new panel indicator which is used to provide a way to respond to messaging events, such as email and IRC pings. If someone IM’s you, then you should see an ephemeral notification, and the messaging indicator will give you a way to respond immediately. Same for email. Pidgin and Evolution are the primary focuses of the work, over time we’ll broaden that to the full complement of IM and email apps in the archive - patches welcome :-)

There will be rough patches. Apps which don’t comply with the FreeDesktop.org spec and send actions on notifications even when the display agent says it does not support them, will have their notifications translated into alerts. That’s the primary focus of the effort now, the find and fix those apps. Also, we know there are several cases where a persistent response framework is required. The messaging indicator gets most of them, we will have additional persistent tools in place for Karmic in October.

---

### Post by damis648 on 2009-02-21
This has already been implemented for some time.

---

### Post by cariboo on 2009-02-21
Here is a picture of the sound notification when using the volume up/down keys on my keyboard

Jim

---

### Post by damis648 on 2009-02-21
> **cariboo907 said:**
> Here is a picture of the sound notification when using the volume up/down keys on my keyboard

Jim

Definitely looks much more professional and cleaner than the current one. :popcorn: The bar in the current one moves way too unpredictably.

---

### Post by AliTabuger7 on 2009-02-21
video demonstration:
[http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf](http://www.markshuttleworth.com/wp-content/uploads/2008/12/jaunty904_notifications_example1_web_092.swf)

Does anyone else find it a little bit ironic that its a flash video?

I don't like the theme of it, but love the ideas, and it is a mockup. THe transparency when hovering over makes them much less obtrusive.

---

### Post by mc4100 on 2009-02-21
Here's another one (Yay, I fixed the blur on my Intel chip ... well, all I could get was mipmap)

---

### Post by Giant Speck on 2009-02-21
Well, if it replaces those tacky notification bubbles, and looks nice on my desktop, then I'm all for it.

---

### Post by Eclipse. on 2009-02-21
> **damis648 said:**
> This has already been implemented for some time.

Your wrong, it only got in to Jaunty a few days ago, I think your getting mixed up with something else.

---

### Post by spupy on 2009-02-21
Brace yourselves, imminent impact with a strong they-stole-it-from-os-x wave!

---

### Post by Luke has no name on 2009-02-21
Brace yourself, imminent impact of a this-is-irrelevant-why-aren't-we-focusing-on-making-programs-that-work-and-not-make-the-shiny-volume-button-our-selling-point-for-example-making-two-desktops-available-in-one-X-session-or-improving-the-media-players-or-getting-compiz-to-not-suck-or-something-along-those-lines wave!

---

### Post by Skripka on 2009-02-21
> **Giant Speck said:**
> Well, if it replaces those tacky notification bubbles, and looks nice on my desktop, then I'm all for it.

Don't worry-they'll make them poo-colored in no time.  Whoops.  Wrong thread. ;)

---

### Post by sharkbaitbobby2 on 2009-02-21
Though it took a little modification, (see attached diff) I like it. Works great on Hardy. :)

---

### Post by kevin11951 on 2009-02-21
> **sharkbaitbobby2 said:**
> Though it took a little modification, (see attached diff) I like it. Works great on Hardy. :)

what did you do to get it in hardy?

---

### Post by Giant Speck on 2009-02-22
Is the new notification thing at least themable?  I mean, is there some sort of configuration file I can edit and change, say, the color?

---

### Post by Skripka on 2009-02-22
> **Giant Speck said:**
> Is the new notification thing at least themable?  I mean, is there some sort of configuration file I can edit and change, say, the color?

Face it.  Your notifications will be poo-colored.  Get over it.  Now.


Dmn...how do I keep posting these in the wrong thread ;)

---

### Post by wersdaluv on 2009-02-22
How do I install this on Intrepid? :D

---

### Post by ELD on 2009-02-22
They won't be poo coloured in koala when we get a new defualt theme heh.

---

### Post by Hells_Dark on 2009-02-22
> **wersdaluv said:**
> How do I install this on Intrepid? :D

+1 :) 
I like that :)

---

### Post by sharkbaitbobby2 on 2009-02-22
Install these packages. There may be more, I'm not sure.
```
sudo apt-get install bzr libglib2.0-dev libgconf2-dev libdbus-glib0-dev libdbus-glib-dev libgtk2.0-dev libx11-dev

```

Download my patch, then run these commands in a terminal:
```

bzr co lp:notify-osd
cd notify-osd
patch -p0 < /path/to/hardy.txt
./autogen.sh
make
sudo make install

```

It installs in /usr/local/libexec/notify-osd, and I think it starts automatically when you log back in. If not, go to system->preferences->sessions and add it there.

---

### Post by Hells_Dark on 2009-02-22
> **sharkbaitbobby2 said:**
> Install these packages. There may be more, I'm not sure.
```
sudo apt-get install bzr libglib2.0-dev libgconf2-dev libdbus-glib0-dev libdbus-glib-dev libgtk2.0-dev libx11-dev

```

Download my patch, then run these commands in a terminal:
```

bzr co lp:notify-osd
cd notify-osd
patch -p0 < /path/to/hardy.txt
./autogen.sh
make
sudo make install

```

It installs in /usr/local/libexec/notify-osd, and I think it starts automatically when you log back in. If not, go to system->preferences->sessions and add it there.

Works for intrepid too ?

Edit : well, failure at make..

---

### Post by sharkbaitbobby2 on 2009-02-22
> **Hells_Dark said:**
> Works for intrepid too ?

It should. If not, post what went wrong here.

---

### Post by Hells_Dark on 2009-02-22
> **sharkbaitbobby2 said:**
> It should. If not, post what went wrong here.

It worked,  i forgot to install libnotify :)

Edit : after the X restart, it doesn't seem to have been launched

Edit : /usr/local/..etc don't do anything 
how to stop the old daemon ?

Edit : a tutorial : [http://blog.alexrybicki.com/2009/02/how-to-install-notify-osd-in-intrepid.html](http://blog.alexrybicki.com/2009/02/how-to-install-notify-osd-in-intrepid.html)

Edit 4 : but it doesn't work for the audio notification (yet?)

---

### Post by Afoot on 2009-02-22
Video: [http://www.youtube.com/watch?v=A8KTwHdonrg](http://www.youtube.com/watch?v=A8KTwHdonrg)

---

