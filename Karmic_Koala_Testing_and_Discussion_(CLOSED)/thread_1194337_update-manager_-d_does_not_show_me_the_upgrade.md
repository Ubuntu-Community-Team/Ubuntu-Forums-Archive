---
title: "update-manager -d does not show me the upgrade"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gp. on 2009-06-22
Hey,
I'm trying to upgrade from jaunty to karmic testing, and I am doing Alt + F2 then typing update-manager -d

it loads up, but it doesn't show me an upgrade button?

---

### Post by LowSky on 2009-06-22
type the command in a terminal instead and see what erros you get and report them.. also the beginer forums are not supposed to be used for quesiton regarding alpha releases, use the developement section

thanks

---

### Post by Gp. on 2009-06-22
Tried that, same result.
Apologies for the wrong area.

---

### Post by Mornedhel on 2009-06-22
I don't believe Karmic will show in update-manager since it hasn't been released yet and is far from stable. New users would try to upgrade to it right away and would probably not like the results.

---

### Post by celticbhoy on 2009-06-22
Have a look at this thread here :-

[http://ubuntuforums.org/showthread.php?t=1143982&highlight=upgrade](http://ubuntuforums.org/showthread.php?t=1143982&highlight=upgrade)

You should also ask a mod to move this to the Karmic section.

Please note that this is still very early in development and liable to breakages.

---

### Post by Sub101 on 2009-06-22
> **Mornedhel said:**
> I don't believe Karmic will show in update-manager since it hasn't been released yet and is far from stable. New users would try to upgrade to it right away and would probably not like the results.

It is available in update manager

---

### Post by Gp. on 2009-06-24
> **Sub101 said:**
> It is available in update manager

This is my point, it isn't for me.

---

### Post by Starks on 2009-06-24
> **Gp. said:**
> Hey,
I'm trying to upgrade from jaunty to karmic testing, and I am doing Alt + F2 then typing update-manager -d

it loads up, but it doesn't show me an upgrade button?
Just gksudo edit /etc/apt/sources.list

Change all jaunty references to karmic.

---

### Post by shakaran on 2009-06-24
> **Starks said:**
> Just gksudo edit /etc/apt/sources.list

Change all jaunty references to karmic.

I suggest that these change should be asked to the user in update-manager and make it automatically.

---

### Post by budluva04 on 2009-06-25
> **Starks said:**
> Just gksudo edit /etc/apt/sources.list

Change all jaunty references to karmic.

WRONG!!! this is not the right way to upgrade anymore, read the wiki...

[http://www.ubuntu.com/testing/karmic/alpha2#Upgrading%20from%20Ubuntu%209.04]("http://www.ubuntu.com/testing/karmic/alpha2#Upgrading%20from%20Ubuntu%209.04")

```
update-manager -d
```

---

### Post by MacUntu on 2009-06-25
> **budluva04 said:**
> WRONG!!! this is not the right way to upgrade anymore, read the wiki...

Not being the encouraged way doesn't make it wrong.

---

### Post by Starks on 2009-06-25
If update-manager -d or sudo update-manager -d don't work, then editing the repos through sources.list is the only way short of mounting an iso and using apt-cdrom

---

### Post by taavikko on 2009-06-25
> **Starks said:**
> If update-manager -d or sudo update-manager -d don't work, then editing the repos through sources.list is the only way short of mounting an iso and using apt-cdrom

No it isn't, you have to set that every release is upgradable through update-manager, by setting

```
/etc/update-manager/release-upgrades
# default behavior for the release upgrader
#

[DEFAULT]
# default prompting behavior, valid options:
#  never  - never prompt for a new distribution version
#  normal - prompt if a new version of the distribution is available
#  lts    - prompt only if a LTS version of the distribution is available
Prompt=normal
```
Prompt to normal

---

### Post by Starks on 2009-06-25
You can also do that from the software sources app.

---

### Post by taavikko on 2009-06-25
> **Starks said:**
> You can also do that from the software sources app.

Yes you can, and still don't have to resort to manually editing sources.list.

---

### Post by HarmonicaGoldfish on 2009-10-03
Beta was released on Thursday. Trying to upgrade from 9.04 since yesterday. I ALT-F2 update-manager -d gives me update manager but no button for upgrade. Same result when I try to run it from terminal.

In Update manager setting the release upgrade is set to normal, the selected ubuntu updates are 'important security' and  'recommended' (Jaunty).

I have never had to change my sources list when doing an upgrade before. Do I have to do that this time?

Thanks,
Any help appreciated!

---

### Post by HarmonicaGoldfish on 2009-10-03
Am upgrading via 

sudo do-release-upgrade -d

don't know why update-manager isn't managing the upgrade but this seems to be working.

---

