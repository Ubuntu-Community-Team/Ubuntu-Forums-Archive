---
title: "SDDM persistent live install, stop auto login"
date: 2016-04-22
forum: Installation &amp; Upgrades
---

### Post by v1sual-3rr0r on 2016-04-22
I have a persistent live install using a casper-rw partition of Kubuntu 16.04. It is running very well, but I would like to disable the live user from logging in automatically. I made a new user account but no matter what settings I set (disable auto login, change auto login) it starts up and just appears to bypass the desktop manager and logs right in to the live user. I have done a lot of searching and have not found a way around this. There is no sddm folder and editing sddm.conf and removing all of the auto login entries does not help. Trying other login managers does not seem to help either. I tried Lightdm and it just goes blank, slim loads but I cannot login to my account with it.  I had similar issues with 15.10 as well... Any help would be appreciated!

---

### Post by sudodus on 2016-04-22
Live systems are made like that. They log in automatically to the live user.

Maybe you should use a portable installed system (in an external drive) instead of a persistent live system. See the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

---

### Post by v1sual-3rr0r on 2016-04-22
I do understand the difference. I know it is possible and I am willing to do some editing of configs, etc. Installing Kubuntu takes over 5 gigs of space and live with persistence takes less than half and on a small drive it does make a difference. You can create additional account that do work in a live install with persistence.  However logging out of the live user into the created user is not ideal.

---

### Post by sudodus on 2016-04-22
I see.

I have never done what you want to do, and I cannot help much. Let us hope [COLOR="#0000CD"]**someone else**[/COLOR] will chip in and help you with this task :-)

---

### Post by v1sual-3rr0r on 2016-04-22
I hope so as well! I have seen some older posts for other variants but not Kubuntu,

---

### Post by yancek on 2016-04-22
I misread your other post which looks pretty similar to this.  I thought you were using Lubuntu and I got the disable autologin to work on that.  I don't know if the link I posted will help or if Kubuntu has the same configuration files needed since KDE will be a lot different than LXDE.

---

### Post by v1sual-3rr0r on 2016-04-22
No worries Yaneck! I have read the same info that you have and it does not work on Kubuntu. I have tried 14.04, 15.10, and now 16.04. I even tried changing from SDDM to Lightdm but Lightdm does not appear to work correctly. UGH...

---

### Post by v1sual-3rr0r on 2016-04-23
[COLOR=#000000][FONT=sans-serif]If it helps I think sddm is using systemd for the auto login...[/FONT][/COLOR]

---

