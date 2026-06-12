---
title: "[SOLVED] ubuntu/ubuntustudio dmraid"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by CheShA on 2008-05-03
Hi all,

I want to run unbuntustudio on top of a dmraid fakeraid configuration (for raid 0+1). I was wondering if there is any way to install it directly to dmraid using the alternate installer provided by 'studio? 

Alternatively, if I have to install standard Ubuntu hardy, how completely can I convert it to ubuntu studio? Will the ubuntustudio-desktop packages cover it or do i need to manually install and configure rt kernel, jack etc? if so, what packages do I need for a complete conversion?

Thanks for your help.

CheShA

---

### Post by CheShA on 2008-05-13
I have managed to get this done, fairly straight forward using a normal Hardy Live CD, *debootstrap*ping then doing a manual package install to chroot environment.

Packages required to build an Ubu studio (after debootstrap):

linux-image-rt
ubuntu-standard
ubuntustudio-desktop 
ubuntustudio-audio            (optional)
ubuntustudio-graphics         (optional)
ubuntustudio-video            (optional)
ubuntustudio-audio-plugins    (optional)


Add your user to Audio and Admin groups, and configure /etc/limits.conf as per [this post]("http://ubuntuforums.org/showthread.php?t=791566"), and you're pretty much good to go.

---

