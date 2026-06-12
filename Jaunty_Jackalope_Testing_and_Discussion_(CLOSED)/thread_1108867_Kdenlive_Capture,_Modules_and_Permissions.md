---
title: "Kdenlive Capture, Modules and Permissions"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Down8ve on 2009-03-28
I'm no expert, but in order to use Kdenlive, the most promising video editor for us regular users, I had to add the firewire modules to load at boot 

sudo gedit /etc/modules

# I then added these to the file
dv1394
raw1394
ohci1394
ieee1394

After saving I then had to add myself to the "video" group and fix permissions:
sudo adduser scott video

sudo chmod 666 /dev/raw1394

Now I can capture video.  Any way to make all this work by default after installation?  Could be another one of those problems that drives people to Windows.

---

