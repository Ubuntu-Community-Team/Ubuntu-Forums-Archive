---
title: "Upgrade to Edgy - X won't start (i810)"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by brentn on 2006-10-30
I just upgraded to edgy last night, and when I rebooted this morning, X would not start.  

The X log had an error "(EE) module ABI major version (0) doesn't match the server's version (1)"

I am using the i810 video driver

After much searching and trying different things, I finally did an apt-cache search i810, and discovered a package called: xserver-xorg-video-i810

I installed it, and tried restarting gdm, and it worked.

Hope this helps somebody.

---

### Post by dentaku65 on 2006-10-30
This depends probably by the old xserver-xorg-air (the xorg for aiglx in dapper) remove/rename the file /etc/gdm/gdm.conf-custom and reboot the machine 8)

---

### Post by nalle on 2006-10-30
Thank you :)

I had the same problem with an ati driver, so if anyone else has troubles, installing the
xserver-xorg-video- the driver you use 
should work

and check what the gdm -custom file has in it with pico, because your programs use it over the default, and who knows if there are other things in there some program might need...

and an easy way to check if new settings have helped is to use
sudo dpkg-reconfigure gdm

---

