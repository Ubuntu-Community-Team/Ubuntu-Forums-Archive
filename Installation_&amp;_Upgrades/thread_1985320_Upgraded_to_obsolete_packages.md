---
title: "Upgraded to obsolete packages"
date: 2012-05-23
forum: Installation &amp; Upgrades
---

### Post by jw1949 on 2012-05-23
12.04 was fine from USB stick, but when (clean) installed is giving a few problems:

- no window controls
- no side launcher
- Compiz closed unexpectedly

After the Compiz error, system says there are obsolete packages installed, including Unity, compiz-core, compiz and quite a few others and suggests that I update.  

I'm a novice with command line and can't get one anyway - all I can do is browse folders with Nautilus (altF2 does no appear to work).  Could someone please guide me to

(1) get a terminal running
(2) do a software update
(3)  recover the launcher bar
(4) reinstate the window controls

Thanks in advance

---

### Post by wilee-nilee on 2012-05-23
> **jw1949 said:**
> 12.04 was fine from USB stick, but when (clean) installed is giving a few problems:

- no window controls
- no side launcher
- Compiz closed unexpectedly

After the Compiz error, system says there are obsolete packages installed, including Unity, compiz-core, compiz and quite a few others and suggests that I update.  

I'm a novice with command line and can't get one anyway - all I can do is browse folders with Nautilus (altF2 does no appear to work).  Could someone please guide me to

(1) get a terminal running
(2) do a software update
(3)  recover the launcher bar
(4) reinstate the window controls

Thanks in advance

Did you install the actual release or a development version?

Did you look for the 2d version in the login, using the gear next to the line for the password?

---

### Post by jw1949 on 2012-05-23
It was the actual release - I downloaded again yesterday.

At the login, I took the Ubuntu option, not the 2d - I will try that and post back.

---

### Post by jw1949 on 2012-05-23
This seems to work well, thank you.  Now why didn't I know that ?:KS

---

### Post by wilee-nilee on 2012-05-23
> **jw1949 said:**
> This seems to work well, thank you.  Now why didn't I know that ?:KS

There is a additional drivers app in 12.04 as well check it if you have not after you are all up to date, might be a graphic driver there to set you up  for the other session. 

Glad the 2d is working at the least. :)

---

### Post by roelforg on 2012-05-23
Right, i assume you after the upgrade you ran the software updater?
If you can get to a terminal
```

sudo apt-get update
sudo apt-get upgrade

```
(all exactly like that)
will upgrade/update any outstanding updates.

---

### Post by jw1949 on 2012-05-23
Well, I have now run the software updater which asked for a restart.  The system now restarts into another user who must be set to auto login and it goes straight back into ubuntu without the 2d !!!   I think if I wait for 30 or 60 minutes it may force a password entry and I may be able to get back to the login screen from there ?

I do not understand your comments about additional drivers.  What am I looking for and how ?

Thanks to the others for their comments but in Unity3D I seem to have no way to get to a terminal prompt or to force it back to the login screen.

---

### Post by roelforg on 2012-05-23
> **jw1949 said:**
> Well, I have now run the software updater which asked for a restart.  The system now restarts into another user who must be set to auto login and it goes straight back into ubuntu without the 2d !!!   I think if I wait for 30 or 60 minutes it may force a password entry and I may be able to get back to the login screen from there ?

I do not understand your comments about additional drivers.  What am I looking for and how ?

Thanks to the others for their comments but in Unity3D I seem to have no way to get to a terminal prompt or to force it back to the login screen.

Ctrl+Alt+T for terminal (hey, it's still gnome and my unity3d takes that command fine)
And run:
```

sudo service lightdm restart

```to force a logout.

---

### Post by wilee-nilee on 2012-05-23
> **jw1949 said:**
> Well, I have now run the software updater which asked for a restart.  The system now restarts into another user who must be set to auto login and it goes straight back into ubuntu without the 2d !!!   I think if I wait for 30 or 60 minutes it may force a password entry and I may be able to get back to the login screen from there ?

I do not understand your comments about additional drivers.  What am I looking for and how ?

Thanks to the others for their comments but in Unity3D I seem to have no way to get to a terminal prompt or to force it back to the login screen.

There is a app in the menu called additional drivers, sometimes a driver is needed for a graphics card and may show up there for install. Other drivers may show there as well, sometimes it takes the full update to get them shown is all. Look in the 2d in this app.

You also want to be aware of some users tendencies on this forum to just post answers without really doing more than feeding their own ego's rather then from an informed position by asking pertinent questions, this is a worldwide phenomena with people in general. Just be careful in who you trust really.

---

### Post by jw1949 on 2012-05-24
Thank you both for your help - I now have a working 12.04 system and if the weather was not so superb here I would have a bit more time to work on it.

---

