---
title: "Notification Urgency Level Testing with Notify OSD"
date: 2009-06-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-06-21
Thanks to a debugging feature in Notify OSD trunk (not pushed to Karmic yet), we can test to make sure that applications set the correct urgency level when displaying notifications. 

The [Desktop Notification Specification]("http://www.galago-project.org/specs/notification/0.9/index.html"), while specifying [guidelines]("http://www.galago-project.org/specs/notification/0.9/x320.html") for urgency levels, leaves them to the discretion of individual developers, and some applications may report incorrect levels, causing Notify OSD and other notification mechanisms to treat their notifications incorrectly. The Notify OSD design specification includes a "Do not disturb" mode, with two separate event queues (Critical and non-critical) which are treated differently in this mode, thus correct urgency levels are important for providing a consistent experience. 

Given the large number of applications that use notifications, the only way to get this right across the board is through testing and reporting bugs. Don't forget that this is potentially a contribution to upstream projects as well; if the reports/fixes go upstream (if you triage bugs, make sure that happens!), the applications will behave correctly in all distributions, not just Ubuntu.

**How To Test**

[list][*] Add [Mirco Müller's PPA]("https://edge.launchpad.net/~macslow/+archive/ppa") to your sources.list and install the 0.9.14-0ubuntu1~ppa10 version. 

[*] Launch Notify OSD with ```
DEBUG=1 /usr/lib/notify-osd/notify-osd
``` from a terminal. This will enable the debugging mode.

[*] Trigger notifications in the application you want to test. You'll note that the notification bubbles display the urgency in a colored top bar, as seen in [this screencast]("http://people.ubuntu.com/~mmueller/urgency-debug-display.ogg").

[*] If the urgency level seems incorrect, [file a bug report]("http://help.ubuntu.com/community/ReportingBugs") against the application that triggered the notification. Notify OSD's log file (~/.cache/notify-osd.log) can be useful.

The following examples under the "[Urgency Levels]("http://www.galago-project.org/specs/notification/0.9/x320.html")" heading of the specification can give you an idea about correct urgency levels:

> For example, "Joe Bob signed on" would be a low urgency. "You have new mail" or "A USB device was unplugged" would be a normal urgency. "Your computer is on fire" would be a critical urgency. 

The [Notify OSD design specification]("https://wiki.ubuntu.com/NotifyOSD") also has detailed examples of expected urgency levels.
[/list]

Kudos to Mirco Müller for working (and [writing up]("http://macslow.net/?p=311")) on this.

---

### Post by plun on 2009-06-22
Done...  can you clarify consequences if MacSlows whole ppa is enabled ?


deb [http://ppa.launchpad.net/macslow/ppa/ubuntu](http://ppa.launchpad.net/macslow/ppa/ubuntu) karmic main 
deb-src [http://ppa.launchpad.net/macslow/ppa/ubuntu](http://ppa.launchpad.net/macslow/ppa/ubuntu) karmic main 


```
plun@plun-laptop:~$ sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys FF6D1003462167CE

```

 
The following packages will be upgraded:
 ** gnome-power-manager gnome-settings-daemon notify-osd**



It works nevertheless......

** (notify-osd:6216): DEBUG: [2009-06-22T08:22:29-00:00, gnome-settings-daemon, id:0, icon:notification-audio-volume-high (synchronous)]  


:)

---

### Post by 23meg on 2009-06-22
> **plun said:**
> 
The following packages will be upgraded:
 ** gnome-power-manager gnome-settings-daemon notify-osd**


Do enable the PPA. You need gnome-power-manager and gnome-settings-daemon from the PPA for now, due to some changes in trunk that aren't relevant to testing urgency levels (the fixed value indicator behavior, I think for [bug #337820]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/337820"), and proximity-based bubble fades). See Mirco's blog post; testing of and feedback on those changes can be separately useful, but let's keep this on topic.

---

### Post by MacSlow on 2009-06-22
See [http://macslow.net/?p=320](http://macslow.net/?p=320) for the visible outcome of trying out the new notify-osd 0.9.14 in combination with the patched versions of gnome-power-manager and gnome-settings-daemon.

Best regards ...

MacSlow

---

### Post by moomex on 2009-06-23
Disconnecting from a network sometimes shows a normal urgency level and sometimes a "urgent". Also, connecting to a network has a "low" urgency which should be either "urgent" or "normal"

I filed a bug: #[391130]("https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/391130")

[IMG]http://launchpadlibrarian.net/28248583/notify-osd.png[/IMG]

---

### Post by MacUntu on 2009-06-24
How can I start notify-osd in debug mode by default? I've tried to add DEBUG=1 to the 'exec'-part of /usr/share/dbus-1/services/org.freedesktop.Notifications.service but it seems I couldn't get it right.

---

### Post by davideotape on 2009-06-24
> **MacUntu said:**
> How can I start notify-osd in debug mode by default? I've tried to add DEBUG=1 to the 'exec'-part of /usr/share/dbus-1/services/org.freedesktop.Notifications.service but it seems I couldn't get it right.

Fist of all, use ```
sudo killall notify-osd
``` to get rid of any currently running versions. Then use ```
DEBUG=1 /usr/lib/notify-osd/notify-osd
``` from a terminal :D

---

### Post by davideotape on 2009-06-24
> **moomex said:**
> I filed a bug: #[391130]("http://https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/391130")

Looks like that link is borked :S Think you need to get rid of the https

---

### Post by taavikko on 2009-06-24
> **davideotape said:**
> Looks like that link is borked :S Think you need to get rid of the https

Actually the preceeding http:// needs to be removed and add : after https.
LP is using https

---

### Post by MacUntu on 2009-06-24
> **davideotape said:**
> Fist of all, use ```
sudo killall notify-osd
``` to get rid of any currently running versions. Then use ```
DEBUG=1 /usr/lib/notify-osd/notify-osd
``` from a terminal :D

Yeah, that's what I'm trying to avoid.

**Edit:**

I now replaced
```
exec /usr/lib/notify-osd/notify-osd
```
in /usr/share/dbus-1/services/org.freedesktop.Notifications.service with 
```
exec /bin/sh -c "DEBUG=1 /usr/lib/notify-osd/notify-osd"
```
which seems to work.

---

