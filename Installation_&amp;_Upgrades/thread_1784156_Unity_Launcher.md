---
title: "Unity Launcher"
date: 2011-06-16
forum: Installation &amp; Upgrades
---

### Post by Squeeeee on 2011-06-16
I've just installed Ubuntu 11.4 and can not get the Unity Launcher to work. 

In fact, I can't even find Unity on the system! 

The Software center tells me that the application is already installed. 

Gnome is running, but I just can seem to get Unity to run.

Please help!

---

### Post by JRV on 2011-06-16
If your video hardware is not up to the task Natty will default to standard Gnome.

Is your video capable of 3D acceleration?
Are you trying to run Unity on an old computer?

---

### Post by DirtyPC on 2011-06-16
Update

'sudo apt-get install upgrade'

and then update video drivers

then check you have unity selected at login menu

---

### Post by Squeeeee on 2011-06-16
Ho JRV

My laptop isn't very old. It was running on XP Service Pack 3 unit I uninstalled it this morning. It has a Nvidia card that is running on the 3D accelerated driver.

---

### Post by Squeeeee on 2011-06-16
Hi Harrylucas1

Sorry, but I'm not sure what you mean by...

'sudo apt-get install upgrade'

Could you please elaborate?

---

### Post by DirtyPC on 2011-06-16
> **Squeeeee said:**
> Hi Harrylucas1

Sorry, but I'm not sure what you mean by...

'sudo apt-get install upgrade'

Could you please elaborate?
run the terminal
from Applications>Accessories>Terminal

copy and paste that code.

It updates to all the latest packages, could include drivers you need.

---

### Post by Squeeeee on 2011-06-16
> **harrylucas1 said:**
> run the terminal
from Applications>Accessories>Terminal

copy and paste that code.

It updates to all the latest packages, could include drivers you need.

I ran it and got the following error "E: Unable to locate package upgrade"

---

### Post by JRV on 2011-06-18
try:
```
sudo apt-get update
sudo apt-get upgrade
```

Click on the on/off icon in the upper right hand corner.
Select System Settings, the bottom entry on the drop down menu.
Click on Additional Drivers.
You should see a warning message that says:> This driver is activated but not currently in use.Ignore it.

Now log out.
At the log-in screen click on your user name.
Some menus should appear in the panel at the bottom of the screen.
In the Session menu select Ubuntu, and then log in.

---

