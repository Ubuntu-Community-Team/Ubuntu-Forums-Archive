---
title: "Please Help ! Unable to boot intu Kubuntu after update"
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by deekay on 2007-01-11
i installed Kubuntu Linux two days ago.

i did a full upgrade of my Kubuntu system  yesterday and also changed system settings, like enabled auto login, and other general settings.

i reboot computer after all this. now its booting up and showing logon screen, and when i type my user id and password, screen goes blank for a second and logoon screen comes back and it doesnt boot into system. i have tried Failsafe login. that also doesnt boot.

please help me. i need to access some important files within two days.

---

### Post by MontanaMax on 2007-01-11
I've done similar things to myself from time to time, usually when I upgrade a whole bunch of things without restarting X inbetween them, or completely rebooting if it's a kernel level change I've made. It's tricky to figure out where the problem is where they are many things that could be the problem.

That said, these are some general things I do to get back to a working system:

First, at the GRUB menu try booting to terminal or command line. 

If you can get to that point, I highly recommend you stick in a USB drive and copy off the files you need immediately. Even though you'll eventually be able to get back into your desktop, it will make you feel a lot better. At least it does for me.

Then try running the basic package check command and deal with any errors it comes up with first:

```
sudo apt-get check
```

The next thing I'd suspect in your case is a video driver problem - did you recently try to install the nvidia drivers or compiz or beryl or one of those things?

---

