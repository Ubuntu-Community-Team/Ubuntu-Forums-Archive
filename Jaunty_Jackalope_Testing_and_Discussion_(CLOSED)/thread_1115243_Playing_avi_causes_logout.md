---
title: "Playing avi causes logout"
date: 2009-04-03
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ponchorage on 2009-04-03
OK, this is a weird one. No matter which video playing application I use I get the same results. This leads me to believe it is probably a gstreamer problem. When I try to play any avi the first time, the program simply aborts. If I try a second time, I get a black screen (like it has killed X) and then I get pushed to the login screen. I've tried vlc, mplayer, and totem all with the same results. 

Anybody know which log I should look in to debug this? I've tried searching all the logs I am aware of but haven't found anything yet. Anybody else experiencing this? I initially installed from the beta and have been doing sudo apt-get update && sudo apt-get upgrade occasionally with the last time being this morning. So, I'm up-to-date. Didn't have this problem on the same hardware under 8.10.

---

### Post by ponchorage on 2009-04-03
Figured it out (kind of). I'm running the Intel 945GM chipset which is known to have issues apparently on Jaunty. By adding

Option        	"AccelMethod" "uxa"

to the Device section of my /etc/X11/xorg.conf file, it made it so I can play video again. Yeah!

---

### Post by gohu1 on 2009-04-10
hey, i think i might be having the same problem you had.
could you explain what you did in a bit more detail?

---

### Post by ponchorage on 2009-04-10
Not much else to say. Open up the file /etc/X11/xorg.conf. You'll probably need sudo power to do it so, something like this from the terminal:

gksudo gedit /etc/X11/xorg.conf

Then look for the Device section and add this:

Option "AccelMethod" "uxa"

The save the file and logout and back in. Might need a restart but I don't think so.

---

