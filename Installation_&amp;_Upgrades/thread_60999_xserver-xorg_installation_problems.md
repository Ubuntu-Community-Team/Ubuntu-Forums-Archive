---
title: "xserver-xorg installation problems"
date: 2005-08-30
forum: Installation &amp; Upgrades
---

### Post by groucho on 2005-08-30
I'm a complete linux newbie, please bear with me:

Decided to give the install a shot, one of my mistakes may have been selecting none of the graphics resolutions during the install (1024x768 and down were selected by default). After that a few errors scrolled faster than I could read, and the GUI croaked on me, leaving me with the following error messages:

"I cannot start the X server" It is likely it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

Click yes:

Log file: "/var/log/Xorg.0.log
Using config file "/etc/X11/xorg.conf"
Data incomplete in file /etc/X11/xorg.conf
    At least one Device section is required
(EE) Problem parsing the config file
(EE) Error pasrsing the config file

Fatal server error:
no screens found

....

Anyway, it turns out that for whatever reason, my Xorg.conf file is blank. Is there any way to regenerate it without causing things to explode?

I've tried sudo X -configure, but it gives me a message "Missing output drivers. Configuration failed.".

Using an NVIDIA graphics card.. so I'm not sure if that makes a difference?

---

### Post by heimo on 2005-08-30
Sure. Run:
 ```
sudo dpkg-reconfigure xserver-xorg

```



If that's not successful, this may come helpful.
[http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21](http://www.ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

