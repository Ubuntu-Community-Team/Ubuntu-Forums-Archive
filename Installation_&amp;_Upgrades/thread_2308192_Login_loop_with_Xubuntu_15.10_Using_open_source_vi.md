---
title: "Login loop with Xubuntu 15.10: Using open source video drivers"
date: 2016-01-01
forum: Installation &amp; Upgrades
---

### Post by MidnightJava on 2016-01-01
I updated Xubuntu from15.04 to 15.10. The upgrade completed with no errors, but I can no longer login via the desktop. The lightdm login window comes up with my account selected, but when I enter my password it re-displays the login window. I can login to a command line session. I switched from lightdm to gdm, and the same thing happens when I log in.

So it seems that perhaps it's a video driver problem. I had already (on a previous upgrade) removed the proprietary drivers because they weren't compatible with the latest kernel, but I purged them again to be sure, and tried many, many other things. I can't find any way to get the Ubuntu desktop to launch. I removed the proprietary drivers like this:

```
sudo apt-get remove --purge xorg-driver-fglrx fglrx*
sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
sudo dpkg-reconfigure xserver-xorg

```

What else can I do? I know it's not LTS, but I didn't expect the entire GUI to become unusable from an upgrade. My video driver is AMD/ATI RS780L [Radeon 3000]

EDIT: /var/log/Xorg.0.log shows normal loading of open source drivers. Maybe the idea of a video driver problem is a red herring. What else would prevent the startup of the desktop? Any troubleshooting advice would be appreciated.

EDIT: I narrowed down the problem, and still stumped as to a solution. I created another user, and when I log in as that user from the DM, the xfce desktop opens properly. Furthermore, if I open a command line for DISPLAY 0 at ctrl-alt-F1, login as the original user (for which the desktop has not been starting) and start the xfce desktop manually on DISPLAY 1 (startxfce4 -- :1) the xfce desktop launches.

So it boils down to: **how do I make the ****xfce**** desktop start automatically for the original user when logging in via the DM?** I tried using the lxdm display manager, but the same problem occurs. I also looked in detail at all the hidden files in the two user home directories, and I cannot see why the xfce desktop starts for the new user, but not for the original one. I've re-installed and re-configured window systems, window managers, display managers, made changes to [COLOR=#111111][FONT=Consolas]/etc/xdg/xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml/xfce4-session.xml&#8212;&#8212;[/FONT][/COLOR]all to no avail. I can't find any way to make the desktop work as it did before the ill-fated upgrade.

---

### Post by ubfan1 on 2016-01-01
You are on the right track looking at the "hidden" files.  You can copy them to a directory (or delete them), and let them be recreated, like a new user.  Some confs you might want to keep for some programs, so copying them somewhere is safer, you can then bring back the pieces you want.

---

### Post by MidnightJava on 2016-01-01
I had already renamed/removed the hidden files that I thought could play a role. So I went ahead and removed every single one of them, and it didn't help. Also now it fails to load xfce automatically even with the new user account. Not sure if something changed, or I was mistaken. I'm certain it worked originally, but I've been wrong about things I'm certain about before.

What I also know for certain is that my distro is utterly broken after a "successful" upgrade, and I've spent far too many hours trying unsuccessfully to fix it. This has happened more often than not upgrading Ubuntu, which I've been using since 11-04. I think I'm reaching the end of my patience with it, and will switch to CentOS, which I've used at work for years and have never had this sort of problem with.

---

