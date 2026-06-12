---
title: "[SOLVED] Screenlets error"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by Kajong on 2008-02-13
When I try to install screenlets, it appears to install correctly but i cannot make screenlets start when i log in. the console returns the error:
"IOError: [Errno 20] Not a directory: '/home/jack/.config/autostart/WordOfTheDayScreenlet.desktop'"

also it says that daemon can't start up

"Unable to connect or launch daemon. Some values may not be displayed correctly."

---

### Post by jan quark on 2008-02-14
what are your specs?

what version of ubuntu are you using?

do you have compiz enabled?

try to follow this guide and install screenlets once again:
[http://www.screenlets.org/index.php/FAQ](http://www.screenlets.org/index.php/FAQ)

---

### Post by Kajong on 2008-02-14
I still have an error...

[IMG]http://i12.photobucket.com/albums/a248/kajong1/screenshot1.png[/IMG]

Why can't it work on startup? When i try to make the folder manually there is another thing named autostart already.
I have Ubuntu Gutsy Gibbon 7.10 64-bit and compiz is enabled with widget layer

I found out how to manually add screenlets to the Sessions>Startup Programs,but i still don't know how to fix the screenlets-manager...

I got it to work! For anyone who needs help on this subject, refer to the comment by jan quark and what i did to solve this problem below.
All i had to do was make the HOME/.config/autostart folder appear. To do this, i went to System>Preferences>Sessions and added a program to startup when i logged in. After i restarted my computer, the autostart folder was there and screenlets worked

---

