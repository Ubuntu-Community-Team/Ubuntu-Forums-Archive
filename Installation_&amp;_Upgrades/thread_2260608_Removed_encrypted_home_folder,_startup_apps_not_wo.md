---
title: "Removed encrypted home folder, startup apps not working"
date: 2015-01-13
forum: Installation &amp; Upgrades
---

### Post by pingaan on 2015-01-13
Hi,

I wanted to be able to login without auth so I removed the encryption using [this]("http://www.howtogeek.com/116179/how-to-disable-home-folder-encryption-after-installing-ubuntu/") guide.
It seems to be running fine aside from that none of the startup apps are functioning. They start up, as they should, and run in the background, sort of. To be able to run them properly I have to shut them down via System Monitor and then start them backup.

Any ideas? Should I uninstall the apps and reinstall them?

Regards.

---

### Post by MAFoElffen on 2015-01-13
if you go to /home/yourUserName/.config/autostart... and take note of what files are there. They will have a ".deskltop" extension. You can then either delete then or go back through gnome-session-properties to remove them.

Then add them again through gnome-sessions-properties...

You should only have to remove/reinstall them as a last resort.

---

### Post by pingaan on 2015-01-13
That did nt do the trick. I even tried reinstalling the failing apps (found out it wasn't all of them) and still the same.. 
Example: Splashtop is a remote desktop server I'm using on this computer. When added to the startup apps it Ubuntu starts up saying that it's already running but I can't access it, other than shutting it down via system monitor. If I remove it from the startup apps I can start it without it saying that it's already running.
So it's like the startup apps runs twice, or something...

---

### Post by MAFoElffen on 2015-01-13
Sorry. That is just weird. Got me thinking on this one.  Nothing really changed except the encryption.

Pick one. Uninstall it, then re-install... see if that works as a test.

---

### Post by pingaan on 2015-01-14
I removed and purged the app (that is a full uninstall, right?) and then reinstalled it. Still same story.

---

### Post by MAFoElffen on 2015-01-18
Sorry-- Taking 25 credits this semester (6 classes), doing tutoring for the CIS department, have 3 projects and 2 tests due tomorrow.

The only thing I can think of (without being there to diagnose onsite...) is to boot in text mode, get a timestamp in the syslog, start X, then get the last 50 lines of the syslog to post here... sao maybe that might show what is going on... along with the Xorg log.

Get to the Grub Boot menu on boot. Press "E" to edit. Go to end of the kernel boot line (starts with "linux"). Delete "quiet splash". Append with "--verbose debug text plymouth=debug"

It will boot with lots of messages ending to a tty text mode prompt. Enter your username and password to log in. Then 
```

cat /var/log/syslog | tail

```
Look at the last line of output and record the timestamp. It will be within "[" and "]" square brackets at the start of that line... Then
```

startx

```
It will start X and the Desktop without starting the graphical login... At the desktop, press <cntrl><alt><T> to art a terminal session
```

cat /var/log/syslog | tail -n 100 >> ~/Documents/syslog_debug.txt

```
Attach that file to your next post. Also please post  /var/log/Xorg.0.log
[/code]

---

### Post by pingaan on 2015-01-18
How dare you study instead of helping poor people like me out?! 
Thanks for taking your time.. ;)

Attached files, as requested!

---

### Post by pingaan on 2015-01-19
It just came to me that there are no errors concerning my issues in the logs. I'll upload the correct ones in a bit.

---

### Post by pingaan on 2015-01-19
Here.. Thanks again!

---

### Post by pingaan on 2015-01-24
[COLOR=#000000][I]MAFoElffen seems very busy atm, maybe there's someone else who can check my logs?
Cheers..[/I][/COLOR]

---

### Post by pingaan on 2015-02-01
Bump

---

### Post by pingaan on 2015-02-05
I found something that might be interesting in finding a solution to this problem of mine. 
I tried adding the apps to Startup apps today again and same story. I unchecked them to reboot and start them manually instead but it acted as if they were running already! 

In short: Even if they aren't checked in Startup apps, just as long as they are added in Startup apps it won't work! Is there any other ways to autostart an app with GUI without using the built-in app for starting up apps?

---

### Post by pingaan on 2015-03-01
Bumping again... Maybe I posted this in the wrong subforum?? :<
I tried executing the script via /etc/rc.local as well and same thing happens..

---

