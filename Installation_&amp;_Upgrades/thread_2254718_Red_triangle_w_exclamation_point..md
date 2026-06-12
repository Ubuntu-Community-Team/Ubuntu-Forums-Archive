---
title: "Red triangle w/ exclamation point."
date: 2014-11-29
forum: Installation &amp; Upgrades
---

### Post by CK.rbg on 2014-11-29
I'm a fairly new ubuntu user & have been exploring different programs, etc. that can replace those that I used when I ran windows. Somewhere along the way I've acquired this red triangle w/ an exclamation point up by my applets that says something about an error regarding updates & it could be a network issue. Both my system & my network are up-to-date & otherwise okay, so I'm wondering if someone can help me pinpoint how to get rid of this for good.

Each time I run sudo apt-get update the triangle disappears but it eventually returns. These are the errors I get when I run the update. I'm hoping that herein lies my solution, but where to go from here is a bit over my head. Any help is appreciated.


```
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Fetched 2,249 kB in 9s (242 kB/s)                                              
W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/openshot.developers/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/trusty/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ppa.launchpad.net/weather-indicator-team/ppa/ubuntu/dists/trusty/main/binary-i386/Packages  404  Not Found
```

---

### Post by Bucky Ball on 2014-11-29
Welcome. Easiest might be to open Software Updater, click Settings in the bottom left of the window, go to Other Software tab and untick the offending repositories (the ones that show the error in your output in the last post). Try first unticking the last ones. You have the openshot.developers PPA installed and the weather-indicator-team PPA installed which a regular user shouldn't really need (unless you have a specific reason). 

Openshot is available already in the Software Centre (and you don't need the devs PPA unless you're a developer) and you are really on after the Weather indicator applet (which should be available if you right click the taskbar and 'Add New Item'. If not, you'll also find that in the Software Centre with a bit of a search.

Good luck and let us know if you need more help with it. ;)

PS: Presuming you're using Trusty Tahir? The 64bit version or the i386? You have the main package repos for both installed as these are causing issues, too:

```
Err http://ppa.launchpad.net trusty/main amd64 Packages                        
  404  Not Found
Err http://ppa.launchpad.net trusty/main i386 Packages                         
  404  Not Found
```

Did you install them manually? If so, I'd kill them too, for the moment. 

A quick tip: best to refer to the Software Centre first rather than installing PPAs. Best to avoid them unless necessary for a number of reasons (they are not officially supported by Ubuntu and therefore should be used with a little caution and they could also be unsuitable for your install/hardware).

After all this, run update again and let's see what happens.

---

### Post by CK.rbg on 2014-11-29
I am running Trusty Tahir. As far as the 2 errors you listed above, I'm not really sure what they are or what they're referring to (or how they got there, for that matter). I generally install most of my apps via the Software Center but occassionally I'll install things using the terminal.

I unticked the Openshot & Weather Indicator in the Software & Updates menu, as you suggested, & ran sudo apt-get update again & no errors were listed of any kind. The 404 not found errors are gone too... as is the red triangle. I'll let you know if any of the issues return but it appears to have been a quick fix. Many thanks.

---

### Post by Bucky Ball on 2014-11-29
Excellent news and glad I could help. To get the machine right up to date, you may like to:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

This won't take you to 14.10 but will update/upgrade any and all software that needs it in your currently installed OS (Trusty).

Thanks for marking as solved and good luck. ;)

---

### Post by CK.rbg on 2014-11-29
Thanks again... and I appreciate the extra pointers.

---

