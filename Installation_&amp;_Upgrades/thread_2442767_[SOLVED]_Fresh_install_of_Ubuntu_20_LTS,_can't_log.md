---
title: "[SOLVED] Fresh install of Ubuntu 20 LTS, can't login after first reboot"
date: 2020-05-07
forum: Installation &amp; Upgrades
---

### Post by altmann-ta on 2020-05-07
[SOLVED]
Fresh install, tried multiple times with a couple of USBs to make sure system wasn't corrupt. Tried another install drive. 

Everytime I fresh install and reboot I can no longer login with correct password. 

Switching teminal allows login to CLI,

Found similar articles online under 'boot loop' which say change permissions of xauth but when doing so it returns error saying no xauth file found. Definitely in the correct home directory.

Please community! Help me!

---

### Post by altmann-ta on 2020-05-07
Autologin broken on installations with an Nvidia GPU using the proprietary driver, so if you selected automatic log in during setup that could be your issue.

If that's the case, you can either re-install and _not_ select autologin when you set up your user or switch the display manager to lightdm which doesn't have the problem. That's pretty easy:

- reboot the machine. The display manager cannot be running during this procedure

- at the password screen do not enter your password. Open a command console (<ctrl><alt><F3>) and log in there with your user credentials. You'll see some administrivia and then a blinking cursor command prompt.

- run the command
Code: [View]

sudo dpkg-reconfigure lightdm

and select lightdm at the prompt. Use the tab key to highlight "OK" and <enter>

- at the command prompt run the command
Code: [View]

reboot -n

to perform an immediate reboot.

When the password screen appears again, you should be able to long in normally. You can use lightdm as your daily driver. If you want to use the default gdm3. go to your user settings and toggle off the option to login automatically. Then repeat the sequence of steps above, this time selecting "gdm3" as the display manager option.

---

### Post by altmann-ta on 2020-05-07
To enable automatic user login from command line as and administrative user edit the /etc/gdm3/custom.conf file from:

[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1

To:

[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login
AutomaticLoginEnable = true
AutomaticLogin = linuxconfig

Once ready, reboot your system to confirm the settings:

$ sudo reboot

---

