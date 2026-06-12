---
title: "Software updater"
date: 2019-08-05
forum: Installation &amp; Upgrades
---

### Post by Dave67 on 2019-08-05
This issue I seen before, I would like to know why this occurs. After I perform updates with the software updater. If I refresh it it states software up to date. If I go to the Command line and use  upgrade I get this result.
for some reason these are not seen by the software updater.

 ```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gir1.2-gst-plugins-base-1.0 gstreamer1.0-alsa gstreamer1.0-gl
  gstreamer1.0-gtk3 gstreamer1.0-libav gstreamer1.0-plugins-base
  gstreamer1.0-plugins-base-apps gstreamer1.0-plugins-good
  gstreamer1.0-plugins-ugly gstreamer1.0-pulseaudio gstreamer1.0-x
  libgstreamer-plugins-good1.0-0
12 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,197 kB of archives.

```

---

### Post by oldfred on 2019-08-05
My default settings in Software updater are to check daily, download & update Security updates automatically  and display other updates weekly.

So are you getting the weekly updates that are not security updates?

---

### Post by Dave67 on 2019-08-05
Yes I am getting them but after I do a software updater. I check the with the command line apt and I see more which the updater does not.

---

### Post by cruzer001 on 2019-08-05
Phased Updates?

[https://wiki.ubuntu.com/PhasedUpdates](https://wiki.ubuntu.com/PhasedUpdates)

---

### Post by Dave67 on 2019-08-06
After read about phase updates maybe those updates above in the code are not ready yet to be installed. I will if is update manager discovers them in future updates.

---

