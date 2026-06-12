---
title: "Problem after Feisty Upgrade to Gusty"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by mslovak on 2007-10-18
Did an upgrade and everything seemed to go well. Upon reboot I end up in terminal mode and then receive the following diagnostic

etc/gdm/failsafeXServer line 47 [: too many arguments

Could not retrieve EDID because get edid is not installed(1)

Line 47 in the file says 

(47)     if [ -z $serverargs ]; then
(48)      # Use :10 to avoid overwriting the (failed) Xorg.0.log
(49)       serverargs = ":10"
(50)    fi

Which leads me to believe that the upgrade somehow damaged my xorg.conf file.

Any suggestions would be appreciated

---

### Post by mattpker on 2007-10-18
Did you have any special drivers or anything?

---

### Post by bjarneh on 2007-10-18
try to reconfigure xorg

sudo dpkg-reconfigure xserver-xorg

see what happens :-)

---

### Post by mslovak on 2007-10-18
Thank you - that fixed it.

Upon investigation I noticed that the log contained an error regarding an incompatibility with the fglrx drivers.

I should have realized that reconfiguring X.org would do the trick. Thank you very much for your help!

Marc

---

### Post by jlulu on 2007-11-04
I have met this issue too, after have making that bjarneh said, all is ok.
Thank you all ...

---

### Post by Irontux on 2007-11-06
I have nvidia card (6600gt).

I have the same problem. 
I Try to reconfigure serverX with "sudo dpkg-reconfigure xserver-xorg" ?

---

