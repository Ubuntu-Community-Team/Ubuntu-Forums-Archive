---
title: "Thunderbird 3 installation help"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by Crash~Override on 2009-12-12
So, I just downloaded the thunderbird 3 from mozilla's website and I was wondering how do I install it?

Any help will be very much appreciated. Thanks

---

### Post by aysiu on 2009-12-12
Here you go:
[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

---

### Post by Crash~Override on 2009-12-12
> **aysiu said:**
> Here you go:
[http://www.psychocats.net/ubuntu/thunderbird](http://www.psychocats.net/ubuntu/thunderbird)

okay so I used the code from the site you mentioned...
```
if [[ ! -f /usr/bin/thunderbird ]]; then sudo apt-get update && sudo  apt-get install thunderbird; fi && if [[ -e ~/.mozilla-thunderbird ]];  then cp -R ~/.mozilla-thunderbird ~/.mozilla-thunderbird.backup; fi &&  if [[ -e ~/.thunderbird ]]; then cp -R ~/.thunderbird  ~/.thunderbird.backup; fi && sudo tar -jxvf thunderbird-3*.tar.bz2 -C  /opt && rm thunderbird-3*.tar.bz2 && sudo dpkg-divert --divert  /usr/bin/thunderbird.ubuntu --rename /usr/bin/thunderbird && sudo ln - s /opt/thunderbird/thunderbird /usr/bin/thunderbird && sudo dpkg- divert --divert /usr/bin/mozilla-thunderbird.ubuntu --rename  /usr/bin/mozilla-thunderbird && sudo ln -s  /opt/thunderbird/thunderbird /usr/bin/mozilla-thunderbird
```After entering the code i got the following error when I tried to launch thunderbird

```
"Could not launch 'Mozilla Thunderbird Mail/News'
Failed to execute child process
"thunderbird" (No such fire or directory)
```

EDIT: I created the folder thunderbird in the /usr/bin/ directory...and now i keep getting permission denied error message when i try to open thunderbird

---

### Post by wilee-nilee on 2009-12-12
I think the PPA at the bottom of the psychocats page is the easiest way of installing. I tried the script install without seeing that the targz had to be in home 1st and had no luck. The I don't think the PPA is as up to date as the Mozilla download but it still works fine.

I think aysiu will help you with the Mozilla install if given enough time.

---

### Post by Crash~Override on 2009-12-12
Actually I just figured it out...After using the code I actually looked at the code to see what it did..I got it working...I just had to update the command in the launcher properties...
It was set to "thunderbird %u". I just changed it to "/opt/thunderbird/thunderbird" and it worked.

But thanks anyways.

---

### Post by aysiu on 2009-12-12
Sorry. For some reason, a space creeped into one of the commands (between the *-* and the *s*).

Should be fixed now.

---

### Post by Sejanus on 2009-12-12
So much for Ubuntu being "as good as windows" for regular user... ;) 

Thanks for this command, it finally did the trick after I spent some one hour looking for how to install that downloaded thunderbird 3...

---

### Post by thuerrschmidt on 2009-12-13
The easiest way to install Thunderbird 3.0 in Karmic is by using the [Mozilla Beta PPA ]("https://launchpad.net/~micahg/+archive/mozilla-beta"). As of today it has Shredder RC3, which is by all practical means identical to the final Thunderbird 3 release.

The build from this PPA will integrate better into your Ubuntu and look much nicer than Mozilla's own. Plus, unlike the [Mozilla Daily Build PPA]("https://launchpad.net/~ubuntu-mozilla-daily/+archive/ppa"), you'll only get milestone releases, not daily updates.

@Sejanus: Declaring Ubuntu inferior to Windows whenever something doesn't work as you expect, even half-jokingly, is considered bad manners around here. Don't do it. It's trolling and won't make you any friends.

---

