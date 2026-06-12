---
title: "Can't save X to configuration file"
date: 2010-01-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jerrynewt on 2010-01-28
Still trying to get second monitor(TV)set up with no luck so far. After configuring X Server Display in Nvidia X Server settings, enabling Xinerama and hitting apply, I try to save to X configuration file and get a box notifying me " Unable to open X config file '/etc/X11/XF86Config' for writing." I have opened the file as administrator and given root and myself read-write priveliges but same result. Hp 9000dv {specs in signature}only has s-video and hdmi outputs, and TV only has s-video. Any ideas how to get the file to accept the new configuration ??

---

### Post by Woody1987 on 2010-01-29
The file should be /etc/X11/xorg.conf not /etc/X11/XF86Config

---

### Post by Grenage on 2010-01-29
Sometimes (for reasons unknown to me) I have to rename or just remove the old xorg.conf file before nvidia-settings will save it.

---

### Post by phenest on 2010-01-29
Get it to show the preview and copy & paste.

---

### Post by realzippy on 2010-01-29
> **Grenage said:**
> Sometimes (for reasons unknown to me) I have to rename or just remove the old xorg.conf file before nvidia-settings will save it.

yep,you have to delete existing file:

**sudo rm /etc/X11/xorg.conf**

then make new one:

**sudo nvidia-xconfig**

to make settings:

**gksudo nvidia-settings**

apply,save to X configuration file....

---

