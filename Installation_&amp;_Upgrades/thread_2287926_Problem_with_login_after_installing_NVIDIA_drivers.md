---
title: "Problem with login after installing NVIDIA drivers"
date: 2015-07-23
forum: Installation &amp; Upgrades
---

### Post by Constantinus_Spin on 2015-07-23
Hello. After having downloaded and successfully installing 352.21 NVIDIA drivers manually (using terminal mode), i restarted ubuntu (14.04). At first the login screen had resolution  1600 X 900, but when i entered my username and password, it tried to load my account, but somehow returned to the login screen (now with lower resolution). Despite entering correct username and password, i cannot get into my account and rebound back to login after every entry of username and password. What could be the problem?

---

### Post by ubfan1 on 2015-07-23
Can you login using the "Guest Session"?  Could be some old config files (ones starting with a dot) are causing problems.  Can you use the "nomodeset" keyword on the grub "linux" boot line to login?  Can you still login from a virtual terminal (crtl-alt-F2)  (function key 2)?  Try deleting the .Xauthority file in your home directory as a start.

---

### Post by SeijiSensei on 2015-07-23
Sometimes this happens if the permissions are wrong on your home directory.  If you can't solve the problem any other way try booting into "recovery mode," then choosing "root shell" when you are offered the option.  Then run:
```

mount -o remount,rw /
cd /home
chown username:username username -R
exit

```
replacing "username" with your own login name, then reboot.  Any better?

---

### Post by Constantinus_Spin on 2015-07-24
Ubfan1, even guest session failed. I deleted .Xauthority file and nothing happened.  I can stil login from a virtual terminal

---

### Post by Constantinus_Spin on 2015-07-24
[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") i did execute the instruction you gave me, but when i got the login screen and then typed username and password and it loaded a green screen, then i restarted the computer and then it couldn't even load the login screen

---

### Post by SeijiSensei on 2015-07-24
> **Constantinus_Spin said:**
> [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195") i did execute the instruction you gave me, but when i got the login screen and then typed username and password and it loaded a green screen, then i restarted the computer and then it couldn't even load the login screen

If you booted into recovery mode, you would not have been asked for a username and password.  To get into recovery mode you have to select it from the menu of options that appear at boot.  If you don't see such a menu, hold down the shift key while booting.

---

