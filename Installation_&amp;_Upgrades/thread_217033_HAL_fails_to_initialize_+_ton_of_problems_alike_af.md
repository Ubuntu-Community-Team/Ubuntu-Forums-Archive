---
title: "HAL fails to initialize + ton of problems alike after upgrading."
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by kwatz on 2006-07-16
I am quite newb to Linux, but am making what you could call good progress with Ubuntu. So far everything's going swell, except for the day i decided to do an upgrade to Dapper. After booting i got an alert popup window, saying: 

"HAL failed to initialize!"

and another one, saying

"Power Manager 
This program cannot start until you start the dbus system service. 
It is strongly recommended that you reboot your computer after starting messagebus."

To add to the annoyance, i get the last mentioned message twice when logging out, and i have to wait about 30 secs for it to go away before being able to log out. (They have a cancel button but it cannot be clicked.)

I tried starting dbus from CLI and pulled all the tricks a hardened windows veteran knows, removing & reinstalling and so on, but nothing worked. So i turned to google and found these: 

[http://ubuntuforums.org/showthread.php?t=213007](http://ubuntuforums.org/showthread.php?t=213007)
[http://www.ubuntuforums.org/showthread.php?t=174445](http://www.ubuntuforums.org/showthread.php?t=174445)

Both of them refer to HAL conflicting with network-mounted Samba shares. I have Samba installed, but i couldnt get it to work originally with my other Windows computer so i left that project alone to concentrate on more important matters (like trying to write cd .. instead of cd.. and so on..), but i didnt have any mounted shares. I disabled the shared folders i had on my pc anyway and noticed that Samba had some strange problems too. Upon /usr/bin/samba stop, it gave out "log_daemon_msg: line 48: etc/init.d/samba command not found" and various other line:X errors. I get the same error trying to start/stop HAL, or the dbus service. During boot, i noticed that Apache also produces alot of log_daemon_msg errors but it works neverthless. 

I guess there is a general solution to all these problems instead of tedious per-application problems, but i have no idea where to start. I have spent alot of time studying this problem, but right now i am in a dead end.

So far i have removed and reinstalled HAL components, Samba and Apache. The error occurs even if Samba is not present at all.

Having popup errors during boot is something that reminds me of the time i used Windows 98, and it's causing me traumatic flashbacks. ANY help is really appreciated.

---

