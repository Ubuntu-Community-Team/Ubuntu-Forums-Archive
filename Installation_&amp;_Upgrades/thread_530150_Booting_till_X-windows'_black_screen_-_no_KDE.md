---
title: "Booting till X-windows' black screen - no KDE"
date: 2007-08-20
forum: Installation &amp; Upgrades
---

### Post by Oceanic on 2007-08-20
Dear fellow (k)ubuntians,

After a month of happily using Kubuntu feisty, suddenly it goes wrong.

Booting goes** till** the black screen with the x shaped cursor of X-windows, then totally black and with the x-shaped cursor etc etc. Guessing with the little knowlegde of linux I have that X-windows is starting and crashing over and over and over...

I have tried recovery modes, also of previous kernels. At some point I can
1) give my root password
2) continue with control d
Control D didn't resolve the issue...
and with option one, well I have no clue what to type :confused:


Thanks very much in advance, your help is greatly appreciated !

---

### Post by TheWizzard on 2007-08-20
look into the log files

you can use ctrl+alt+F1 to to login

next, type 
```
tail -f /var/log/Xorg.0.log
```

this should tell you what's happening.

---

### Post by Oceanic on 2007-08-20
Thank you TheWizzard !!!

While the x was crashing and starting I wasn't able to get to the login,
but I went to the recovery mode instead and waited till I was allowed to log in as root.

Took me some time to realize that the o was a 0 (zero) <blush>

anyway, below the cryptic reply:

Cheers, much appreciated!

[COLOR="Red"]Error opening /dev/wacom: No such file or directory
(EE) xf86OpenSerial : cannot open device /dev/wacom
               no such file or directory
Error opening /dev/wacom : No such file or directory
(EE) xf86OpenSerial : cannot open device /dev/wacom
               no such file or directory
Error opening /dev/wacom: No such file or directory
(II) configured Mouse: ps2EnableDataReporting: succeeded
Could not init font patch element /usr/share/fonts/X11/Cyrillic, removing from list!
Could not init font patch element /usr/share/fonts/X11/Type1, removing from list![/COLOR]

---

### Post by TheWizzard on 2007-08-20
the xf86OpenSerial error happens also to me, so i don't think that's the problem.

use google to search for the error messages. i found this one:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/91351](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/91351)


i'm not sure if the information you posted is sufficient because i don't see a report of a crash. like "Server aborting" 
you may want to search the logfile for messages like this. 

good luck

---

### Post by Oceanic on 2007-08-20
Thanks TheWizzard,

Indeed, the log didn't mention a crash (everything that was returned is copied in my previous post)

did install msttcorefonts recently yet have rebooted without problems many times since then.

Cheers...

---

### Post by chrysemys on 2007-08-20
Sounds more like a KDE problem than an X-server problem to me.

Do you recall changing something basically in KDE? like an upgrade ore some configuration change?

One could try renaming (-removing-) one's .kde* file's (losing presciously tunded but reconfigurable kde settings)

rgds

---

### Post by Oceanic on 2007-08-21
Well, retracing my steps:

[COLOR="Red"]sudo wget [http://www.medibuntu.org/sources.list.d/feisty.list](http://www.medibuntu.org/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list
wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update[/COLOR]

and
[COLOR="Red"]sudo apt-get install libdvdcss2[/COLOR]

and
[COLOR="Red"]
sudo apt-get install w32codecs[/COLOR]

Then from [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[COLOR="Red"]Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. 
Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.[/COLOR]


Does anyone have an idea please?

---

