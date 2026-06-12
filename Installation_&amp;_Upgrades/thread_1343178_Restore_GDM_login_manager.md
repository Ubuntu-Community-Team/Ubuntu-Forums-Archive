---
title: "Restore GDM login manager"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by tombeard on 2009-12-01
I just upgraded to 9.10. Now my login manager is showing the Xubuntu (xfce) login screen. I sometimes use xfce to support other machines, but I would like to restore the gnome login screen. I tried "sudo -u gdm gnome-control-center" but it hangs and I ^c to restore my prompt. Some have said to use System -> Administration -> Advanced, but I do not have that menu item.

---

### Post by RedSingularity on 2009-12-01
Look in system>Admin>Login window

Check "default session" and select "gnome" in the drop down.  See if that works.

---

### Post by tombeard on 2009-12-01
Thanks, but I do not see System Admin Login Window. I do have Login Screen, but that is for setting up automatic login. If I am missing a utility, what do I need to install?

---

### Post by RedSingularity on 2009-12-01
Oh no its not a piece of software.  I mean look in System tab Admin tab and then click Login Window.

---

### Post by tombeard on 2009-12-01
I think I am doing it right. Attached is a screendump.

---

### Post by RedSingularity on 2009-12-01
Yes you are.....what Ubuntu version you running?

---

### Post by tombeard on 2009-12-01
I appreciate your taking the time to help. Please see screenshot.

---

### Post by RedSingularity on 2009-12-02
Ohhhh you are running Karmic.  Maybe they took that tool out in karmic.  Look in synaptic...do you have a program called gnome-session installed?

---

### Post by tombeard on 2009-12-02
Yea, Karmic came with the 9.10 upgrade and everyone says it is responsible. Synaptic says I have gnone-session installed. Can you tell me how to run it? It isn't recognized as a terminal command.

---

### Post by RedSingularity on 2009-12-02
Gnome session might not be the software we are looking for.  Let me do some research.  Stand by for a few minutes.

---

### Post by RedSingularity on 2009-12-02
Do you have xfce installed?

---

### Post by tombeard on 2009-12-02
Yes. I have other computers with xubuntu and I installed xfce on this one so I could work out problems with the others. xfce was a session option (and still is) prior to the upgrade, but the login manager has always been gnome. When I updated to 9.10 the xfce login manager became default and so far I haven't found any way to restore gnome. I understand it is related to karmic, something about using X for logon to reduce session load time. I am still able to start a normal gnome session, it is just that xfce is now the only logon manager available. If I remember correctly, when I first loaded xfce it installed the xfce login manager, but I was able to easily revert to gnome.  That was a couple of years ago so I don't remember how I made the switch back but it was no big deal. It wouldn't be important except that the rest of my family will be confused trying to log onto their accounts when they see the unfamiliar login manager.

---

### Post by RedSingularity on 2009-12-02
Ahh i see.  I have searched other parts of the forum and it would seem that other people as well have encountered this problem with the xfce login prompt.  They said that they have uninstaled xfce, reinstalled gnome, and then rebooted.  Apparently that fixed it for them.  Then after you have the gnome prompt back you can reinstall xfce.  What a shame though.  They have an option in 9.04 to change the login screen.  I dont know why they got rid of it.  It was a handy tool.  Can you at least change your login screen look?  You know like a login wallpaper?

---

### Post by tombeard on 2009-12-02
Thanks for your help. I am looking into installing logon themes; I'll post back if I succeed.

---

### Post by slumbergod on 2009-12-02
Log-in themes only partially fixes the problems with the gdm in Xubuntu. The problem is that the gdm 2.28 is so new that they haven't yet finished it and as a result many of the configuration properties are absent.

Some people using Ubuntu have downgraded to gdm 2.20 (the Jaunty one) and done a manual hack to fix the bug that it has. 

For Xubuntu there is now /etc/gdm/gdm.conf so I don't know if it is possible to downgrade gdm. The irc group is typically rude and unhelpful (why do they say go there for help when the people who answer are geeks with no people skills?)

---

### Post by ravisghosh on 2009-12-12
Any possibility of getting this fixed in the near future for xfce users.

A request: Please change the title and add "login window missing in xfce" so that other people can easily find this thread.

---

