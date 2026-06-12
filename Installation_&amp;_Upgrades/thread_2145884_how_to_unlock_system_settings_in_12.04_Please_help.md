---
title: "how to unlock system settings in 12.04? Please help!!"
date: 2013-05-16
forum: Installation &amp; Upgrades
---

### Post by grashdur on 2013-05-16
Dear All,

I just reinstalled Ubuntu 12.04 after experiencing lots of bugs and performance issues in 13.04. After running the updates, I am unable to change system settings. For example, I want to stop the screen from locking after ten minutes, switch to a 24-hour clock, and change to single-click for opening things. This is horrible, because now I will have to type my login password before I can even answer an incoming phonecall, if I've been away from the computer! Or perhaps I won't even hear it ring now.

I don't know whether "unlock" is even the correct term for my subject line: **I can go into the relevant menus and change any of these settings, but the changes have no effect on the system and are not saved. I have no problems with administrator privileges: I can install new software. It's just the system settings.** I was thinking of trying the Unity Tweak Tool, but that's not in the repositories for 12.04. I tried reinstalling gnome-control-center, but that made no difference.

I couldn't find any information about this problem online, so I just redid the installation. This time the settings are locked even before running the updates, which makes me suspect that this locking-up of settings was saved in some preferences folder in my home partition. So far I haven't found which hidden folder contain those settings.

Oh, and by the way: I just **logged back into my 13.04** (I left it installed in a different root partition), and I saw that **the system clock is missing from the top bar!** Did reverting to an older Ubuntu mess up some settings?

---

### Post by grashdur on 2013-05-16
Update: I discovered that even the launcher is not saving after I reboot! So I can't really use the launcher either!

---

### Post by grashdur on 2013-05-17
After a night of sleep, I thought of just creating a new (administrator) user account. When I did that, the new account's settings worked just fine. So I just copied my files over to the new user folder, and everything works fine now. 

I did have trouble getting writing privileges on files in my old user folder. That's why I decided just to copy them over. But I couldn't get permission to copy them either. Not from within my old user account, and not even as root. So I ended up having to copy them all through external media!

I think what went wrong to start with is that the updates corrupted my user account. And even reinstalling Unity, and reinstalling the OS again, didn't fix the problem, probably because it involved preference files in hidden folders of my home folder.

---

