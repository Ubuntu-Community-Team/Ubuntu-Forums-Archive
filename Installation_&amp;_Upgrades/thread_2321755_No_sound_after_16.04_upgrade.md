---
title: "No sound after 16.04 upgrade"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by ppdjoy on 2016-04-24
I had this issue of no sound after upgrade when I upgraded to 14.04 back in the days. That time, I used [this]("http://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/") suggestion to fix the issue. Although, I must say I had to run the ```
sudo alsa force-reload
``` command every time I booted up the computer. Today, after the upgrade to 16.04, I tried the same method, but to no avail. Surprisingly, I don't see the "dummy output" as before, but testing the speakers, gives me no sound, or even the system doesn't do anything when I do test sounds for left and/or right speakers. 



My computer is a [Thinkpad Lenovo T61]("http://www.cnet.com/products/lenovo-t61/specs/"), FYI.

Please help me fix the issue.

Thanks!

---

### Post by ppdjoy on 2016-04-24
So, after some other maneuverings, I got the sound icon back on the notification tray after it disappeared some time back. Now, the *dummy output* is back but no **Profile** is present.  

[IMG]http://i.imgur.com/lpzgZtI.png[/IMG]

---

### Post by VaclavC on 2016-06-14
I had some PulseAudio misconfigurations in my home dir, deleting (moving to tmp exactly) ~/.config/pulse directory and logout/login helped me.

---

