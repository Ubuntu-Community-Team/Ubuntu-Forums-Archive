---
title: "Installing a 'Firefox only' system"
date: 2012-07-12
forum: Installation &amp; Upgrades
---

### Post by bramw on 2012-07-12
Hello all,
After reading tons and tons of commands, manuals, comments, blogs ... i'm getting fed up with things not working as they should (probably because I don't know enough about it, but still) while what I'm trying to achieve isn't that difficult.
I need to set up a 'browser only' system, which runs obviously a browser (preferably firefox) and a C app in the background. So, from the moment the user pushes the 'power on' button of the device, he should see the browser as soon as possible, without the possiblity of exiting it unless the device is turned off. No login screens, no commands to fill in, no pop-ups, no desktop, nothing. The setup should be as lightweight as possible, since it will be used as an embedded system.
I've already tried installing ubuntu 12.04 together with it's GUI, but I think this is a bit of overkill to install the entire GUI just to get firefox running.
I don't have multiple monitors or anything like that, so the more simple the solution is, the better. So what you can really help me with is some kind of roadmap of the things I should install/execute/submit to get this up and running. Thank you.

---

### Post by Cheesemill on 2012-07-12
Do a search for 'ubuntu kiosk', there are loads of guides out there.

---

### Post by beesthorpe on 2012-07-12
I think what you're looking for is termed a "kiosk browser" system,  maybe a search under that term or "Ubuntu kiosk" might prove productive

oops sorry Cheesemill you beat me to it:)

---

### Post by bramw on 2012-07-12
I have, but the problem with this Kiosk systems is that they almost all install a full desktop environment (like GNOME), and I think this is just overkill to use only a browser. I really need to system to boot up as quick as possible.

---

### Post by oldfred on 2012-07-13
Firefox has to have a gui to run. But you may not need all of it.

Kiosk discussions:
[http://ubuntuforums.org/showthread.php?t=1872560](http://ubuntuforums.org/showthread.php?t=1872560)
[http://ubuntuforums.org/showthread.php?t=1881141](http://ubuntuforums.org/showthread.php?t=1881141)
[http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/](http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/)
chromium kiosk using Tiny Core Linux. Talk about small and light!
[http://ubuntuforums.org/showthread.php?t=1891594](http://ubuntuforums.org/showthread.php?t=1891594)

---

### Post by hovrashko on 2012-07-13
maybe you looking for ubuntuzilla?

---

