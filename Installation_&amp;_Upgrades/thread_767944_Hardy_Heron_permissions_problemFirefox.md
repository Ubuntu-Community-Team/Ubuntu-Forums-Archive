---
title: "Hardy Heron permissions problem/Firefox"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by Tylerofl on 2008-04-26
Hey, after installing Google Earth, my Firefox stopped displaying my homepage on startup, and the Forward, Back, and Stop buttons are permanently gray. I restarted the computer, thinking this would solve it, but it wouldn't let me get back in. I tried going through the recovery kernel, which locked up at ALSA, and then I tried the normal one again, and it took me to the login page.

When trying to log in, I was greeted by a message, something like "User's $HOME/.dmrc file is being ignored," and something about setting permissions to 566. It let me log in, but Firefox still didn't work properly. I followed a solution from somewhere on Google about changing permissions with chmod, and was finally able to get the warning message out of the login screen, but I'm still stuck with a broken Firefox.

I tried removing and installing Firefox again, to no luck. It seems like a petty concern, but whatever I did to cause that permissions problem probably caused deeper issues than just Firefox, and I don't want to screw my system up even more by trying to casually use it.

Thanks in advance!

---

### Post by Cato2 on 2008-05-16
Just in case you are still tracking this...

I've had a similar problem with Firefox 3 beta 5 on Hardy - it initially worked on Live CD, but when I started using it with my Firefox profile from Feisty, the address bar stopped working and the Back button was greyed out, as you describe.  I didn't get any relevant error messages on starting from a console though.

I think this may be a permissions or a profile problem.  You can test this out by creating a new user, using System | Administration | Users and Groups, or just type: ```
 sudo adduser --home /home/test --shell /bin/bash test
```(In fact maybe you can skip the new user part altogether, though it's helpful when troubleshooting generally).

Log on as this user, and see if you get the same problems.  If you don't get the problem, try backing up the whole of your Firefox profile (normally ~/.mozilla) - something like ```
tar czvf ~/firefox-profile.tar.gz ~/.mozilla
``` should work.  Then try creating a new profile with Firefox using Terminal:  ```
firefox -ProfileManager
``` - create one called Test.

Assuming the new profile works, you can either go back to the old profile, deleting extensions etc until something works, or you can compare permissions etc, or simply use the new profile and build that up by adding extensions (probably the best option).

To get your bookmarks back again, see [http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/5e955f28e154a361](http://groups.google.com/group/mozilla.support.firefox/browse_thread/thread/5e955f28e154a361) - basically you need to find the relevant profile folder (use ProfileManager and also check modification times and sizes on the bookmark* and places* files), and copy the relevant files across (from FF3 to FF3 - so you need to ensure the new places* files are copied over).  MozillaZine's wiki is a great source of advice for this sort of thing.

I'm still not sure why FF3 had this problem, and I don't think it should be in an LTS release since it's still beta, but perhaps it will start working now...

---

