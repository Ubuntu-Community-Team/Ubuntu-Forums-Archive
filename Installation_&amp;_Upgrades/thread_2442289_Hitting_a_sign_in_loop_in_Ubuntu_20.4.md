---
title: "Hitting a sign in loop in Ubuntu 20.4"
date: 2020-05-01
forum: Installation &amp; Upgrades
---

### Post by wdavies-39 on 2020-05-01
I'm a newbie and I've just done a clean install of Ubuntu 20.4 and I'm getting stuck in an endless sign in loop. I put the correct user name and password in, I am taken to the desktop for about a second and then bounced back to the sign in page again. Can anybody offer any suggestions please.

---

### Post by rbmorse on 2020-05-02
Autologin broken on installations with an Nvidia GPU using the proprietary driver, so if you selected automatic log in during setup that could be your issue. 

If that's the case, you can either re-install and _not_ select autologin when you set up your user or switch the display manager to lightdm which doesn't have the problem.  That's pretty easy: 

- reboot the machine.  The display manager cannot be running during this procedure

- at the password screen do not enter your password.  Open a command console (<ctrl><alt><F3>) and log in there with your user credentials. You'll see some administrivia and then a blinking cursor command prompt. 

- run the command ```
sudo dpkg-reconfigure lightdm
``` and select lightdm at the prompt.  Use the tab key to highlight "OK" and <enter>

- at the command prompt run the command ```
reboot -n
``` to perform an immediate reboot.  

When the password screen appears again, you should be able to long in normally.   You can use lightdm as your daily driver.  If you want to use the default gdm3.  go to your user settings and toggle off the option to login automatically.   Then repeat the sequence of steps above, this time selecting "gdm3" as the display manager option.

---

### Post by wdavies-39 on 2020-05-04
Thanks for your help - that worked. Case solved!

---

