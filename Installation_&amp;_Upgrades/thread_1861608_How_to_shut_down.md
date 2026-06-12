---
title: "How to shut down"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by grantmcduling on 2011-10-15
I have just upgraded to v 11.10 and notice that I now no longer have the system menu icon in the top right hand side of my task bar. This means I can't log off or shut down. How do I now do this? Can I reinstate the system menu there? How do I do this? I have searched the help menu without luck.

Regards
Grant

---

### Post by wi0 on 2011-10-15
Are you saying you don't have a little gear icon? I'll let other people to solve that.
As a temporary measure use this command in terminal: shutdown -h now

---

### Post by grantmcduling on 2011-10-15
Yes, that's right. Thanks for the terminal tip. Worked fine.

---

### Post by lsward on 2011-10-15
You can always hold down Alt + Sys Rq while pressing e, i, o, s, u, b, in sequence and that will shut you down as well.

---

### Post by BazookaAce on 2011-10-15
or: 

```
sudo poweroff
```

---

### Post by wi0 on 2011-10-15
> **lsward said:**
> You can always hold down Alt + Sys Rq while pressing e, i, o, s, u, b, in sequence and that will shut you down as well.

This sequence will shutdown the system right after closing (and if that doesn't work, killing) all processes. No syncing, unmounting or rebooting will take place. 

The correct sequence is: r e i s u o
Switch Keyboard mode, close processes, kill processes, sync, unmount, shutdown. It's better to reserve the use of this sequence for when a system is completely frozen and won't switch to a console(e.g. Alt + Ctrl + F1). In this case the o at the end would probably be replaced with a b for a reboot.

---

### Post by lsward on 2011-10-15
Oh, thanks for pointing that out.  Sorry, I wasn't trying to give bad advice.  I have just dealt with so many lockups that I have gotten use to using that sequence.

---

### Post by MAFoElffen on 2011-10-16
> **grantmcduling said:**
> I have just upgraded to v 11.10 and notice that I now no longer have the system menu icon in the top right hand side of my task bar. This means I can't log off or shut down. How do I now do this? Can I reinstate the system menu there? How do I do this? I have searched the help menu without luck.

Regards
Grant
Many tips have been given, but an answer to the original question is look at the top bar, upper-right most item... the user name.  Click on it with your Mouse cursor. Under it you should see "Shutdown" as the last item.

In a graphical screen, sometimes the "shutdown" item won't show for some reason when the sys is borked... In that case <cntrl><alt><del> usually brings up the Shutdown applet dialog box.

In a terminal
[code]
sudo shutdown -P now
[code]
If you have other boxes or users connected, replace "now" with the number of seconds delay.

If you use the -h flag (like someone suggested, that tells it to halt and it decides on its own whether it goes off or halts.  If it goes halt, the system hangs there... (Past personal experience told me that this is not desirable!)

---

### Post by grantmcduling on 2011-10-16
If I go to the right hand side of the bar at the top and click on my user name, I see the following: Switch user account, Guest session, Grant McDuling, Online account, User account.

If I select guest session, a new screen opens up which does have the gear symbol in the top right hand corner and that I can use to shut down etc. But in my own session screen, that gear symbol is missing. How can I rectify that?

Regards
Grant

---

### Post by atentik on 2011-10-16
Sorry to hack this post but why does my system takes forever to shutdown after upgrade to 11.10? Actually, I have never seen it shutdown on its own... waited for 30min and had to manually shut it down by pushing the power button.

---

### Post by kringle on 2011-10-16
> **grantmcduling said:**
> If I go to the right hand side of the bar at the top and click on my user name, I see the following: Switch user account, Guest session, Grant McDuling, Online account, User account.

If I select guest session, a new screen opens up which does have the gear symbol in the top right hand corner and that I can use to shut down etc. But in my own session screen, that gear symbol is missing. How can I rectify that?

Regards
Grant

I'm having the exact same problem. Anybody find any solutions?

EDIT: Okay, after searching around in some forums to also tackle my missing icons after upgrading, I found someone suggesting to go to Appearance and changing the theme to Radiance. Guess what? Most of my fonts are back and, more importantly, I have the gear and the ability to shut down again. *Ubuntu 11.10 with Unity3D*

Hope this helps.

---

### Post by MAFoElffen on 2011-10-16
> **grantmcduling said:**
> If I go to the right hand side of the bar at the top and click on my user name, I see the following: Switch user account, Guest session, Grant McDuling, Online account, User account.

If I select guest session, a new screen opens up which does have the gear symbol in the top right hand corner and that I can use to shut down etc. But in my own session screen, that gear symbol is missing. How can I rectify that?

Regards
Grant
What desktop are you using?  Unity3D, Unity2D, Gnome, Gnome Classic, Gnome without affects?

---

### Post by grantmcduling on 2011-10-16
How do I check what desktop I am running? I can't see reference to it anywhere.

---

### Post by MAFoElffen on 2011-10-16
> **grantmcduling said:**
> How do I check what desktop I am running? I can't see reference to it anywhere.
How I do it, is when it is booting and you get to the lightdm login screen... Look at that login dialog box. In the upper right corner is a white Ubuntu Icon. Click on it with your mouse.  A dropdown menu will come up, with all the desktop options that are installed.  A little white dot will be in front of the last option selected.  That selected (if you didn't select another) would also be the desktop if you just logged in.

---

### Post by grantmcduling on 2011-10-16
The desktop I am running is Ubuntu.

---

