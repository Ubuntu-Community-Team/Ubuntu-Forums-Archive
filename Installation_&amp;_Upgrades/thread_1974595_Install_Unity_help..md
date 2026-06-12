---
title: "Install Unity help."
date: 2012-05-06
forum: Installation &amp; Upgrades
---

### Post by 1885 on 2012-05-06
I was able to install xubuntu off a usb drive on a hp laptop pavillion b2000\

I have xfce install but I want to switch to unity to try it out.

I install then reboot so I can change the session but only xfce and xubuntu session show up.

How can I get the Unity session to show up on my login?

What else do I need to install?

---

### Post by mips on 2012-05-06
You need to change your lightdm greeter session from *lightdm-gtk-greeter* (as used by xubuntu) to *unity-greeter* as used by ubuntu.

[http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins](http://askubuntu.com/questions/62833/how-do-i-change-the-default-session-for-when-using-auto-logins)

You can also change your session to 
*ubuntu-2d.desktop* for unity 2d
*ubuntu.desktop* for unity 3d

All this information is in the above link.

---

### Post by 1885 on 2012-05-06
thanks for the line.
I did the following : 
sudo /usr/lib/lightdm/lightdm-set-defaults -s ubuntu-2d
and it change the lightdm.conf file but when I reboot I do not get an option to use ubuntu-2d
I check 
root@bulldog00:/usr/share/xsessions# ls -l
total 16
-rw-r--r-- 1 root root 5808 Feb 14 15:34 xfce.desktop
-rw-r--r-- 1 root root 5607 Feb  4 12:04 xubuntu.desktop

No ubuntu-2d ?

What am I missing.  I thought i installed the packages.

thanks

---

### Post by mips on 2012-05-07
Did you change the greeter-session?

```
[SeatDefaults]
**greeter-session=unity-greeter**
user-session=ubuntu-2d
autologin-user=myusername
autologin-user-timeout=0
```

---

