---
title: "Missing toolbar after upgrading packages + gweather removal"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by dbiser on 2012-02-05
There were some important security upgrades available today.  One that caught my attention were upgrades for GWeather.  Since I don't use GWeather, I decided to remove it via the Ubuntu software center.  I removed a total of two GWeather packages this way (library and headers).  I then unchecked the box to upgrade GWeather in the daily upgrade dialog window and I proceeded to upgrade everything else. After restarting my system no tool bars were showing at the top or bottom of my desktop.  That means no time, applications menus, workspace boxes, nothing.

I'm currently running Ubuntu 10.10.

Any ideas on how to get my toolbar back would be greatly appreciated.

---

### Post by aasdfasdfg on 2012-02-05
The toolbars are managed by the gnome-panel application. Ensure that it is running.

---

### Post by dbiser on 2012-02-06
I ran

$ ps -ef | grep gnome-panel
 
which returned empty.  I then tried

$ gnome-panel

and found that gnome-panel was not installed.  I reinstalled it

$ sudo apt-get install gnome-panel

then followed [this]("http://ubuntuforums.org/archive/index.php/t-1604044.html") solution for adding gnome-panel to the startup applications list, which required the following:

"Ctl-Alt-T to pull up terminal.
Type gnome-panel and hit enter.
With your panel running, select System->Preferences->Startup Applications.
Click Add and in the "Command:" line add gnome-panel and click Add.
Click Close."

Now gnome-panel is running at startup and I have my toolbar and application menus visible again.

Thanks aasdfasdfg for pointing me in the right direction!

---

### Post by aasdfasdfg on 2012-02-06
No problem, glad I could help. So it sounds like you may have accidentally uninstalled gnome-panel when you were uninstalling GWeather?

---

### Post by dbiser on 2012-02-06
That's correct.  From the Ubuntu Software Center, I uninstalled libgweather-common and libgweather1.  For somereason this caused gnome-panel to be uninstalled.  Very odd IMO.

I tried uninstalling libgweather-common and libgweather1 from a different computer running Ubuntu 10.10 to see if I could replicate the same problem, and sure enough it did.  So this is the culprit.

---

### Post by aasdfasdfg on 2012-02-07
Actually, this behavior is not a bug. You can see [that]("http://packages.ubuntu.com/lucid/gnome-panel") libgweather is a dependency of gnome-panel. I personally don't know why, but I am sure there is a good reason. If you're still interested in this topic, I would suggest asking the gweather people why this is the case.

---

### Post by matthill11 on 2012-03-02
Thanks for the post thats exactly the info i needed


> **dbiser said:**
> I ran

$ ps -ef | grep gnome-panel
 
which returned empty.  I then tried

$ gnome-panel

and found that gnome-panel was not installed.  I reinstalled it

$ sudo apt-get install gnome-panel

then followed [this]("http://ubuntuforums.org/archive/index.php/t-1604044.html") solution for adding gnome-panel to the startup applications list, which required the following:

"Ctl-Alt-T to pull up terminal.
Type gnome-panel and hit enter.
With your panel running, select System->Preferences->Startup Applications.
Click Add and in the "Command:" line add gnome-panel and click Add.
Click Close."

Now gnome-panel is running at startup and I have my toolbar and application menus visible again.

Thanks aasdfasdfg for pointing me in the right direction!

---

