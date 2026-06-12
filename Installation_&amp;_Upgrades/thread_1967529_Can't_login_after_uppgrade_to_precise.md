---
title: "Can't login after uppgrade to precise"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by potatochip on 2012-04-28
I have just upgrade to 12.04 from 11.10 and can't login.
On the login screen instead of a password box it just says "retry" and if I go to a terminal and try and login I get a "login incorrect" message immediately after entering the username and before being prompted for a password.
Any ideas how I start to try and fix this?

---

### Post by nizamibilal1064 on 2012-04-28
It seems that you have forgotten your id or password....check whether caps is on. Initially login may take quite some time.

---

### Post by potatochip on 2012-04-28
It's not quite as simple as that.
If you read the post you can see that I can't even get to the point of entering my password.

I've removed the autologin line from /etc/lightdm/lightdm.conf and it now shows the box to enter a password but as soon as I login it flashes black and then goes back to the login screen.

From a terminal and via ssh I can login with this account so password is correct.

Other accounts do work from the login screen.

This line comes up in the auth.log;

Apr 28 16:13:29 twistie dbus[1056]: [system] Rejected send message, 2 matched rules; type="method_call", sender=":1.368" (uid=108 pid=15467 comm="/usr/lib/indicator-datetime/indicator-datetime-ser") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination=":1.20" (uid=0 pid=2143 comm="/usr/sbin/console-kit-daemon --no-daemon ")

I'm not sure if that is relevant or not though.

Any ideas?

---

### Post by potatochip on 2012-04-28
Reinstalling ligtdm didn't work but this post did;

[http://ubuntuforums.org/showthread.php?t=1859272](http://ubuntuforums.org/showthread.php?t=1859272)

mv .Xauthority .Xauthority.bak
sudo service lightdm restart

---

