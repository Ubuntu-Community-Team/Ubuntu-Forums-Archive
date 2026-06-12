---
title: "Failed to start the X server"
date: 2006-03-21
forum: Installation &amp; Upgrades
---

### Post by morwyn on 2006-03-21
I am a complete linux noob that could really use some help. The install goes fine,  but when I try to boot into ubuntu, I get this error. "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?" Then, it shows some basic version information (I guess). After that, it takes me back to the login screen.

I am wondering if it is due to the need for nvidia drivers. I found some directions for installing drivers, but it says I have to make sure I have both the universe and multiverse repositories enabled, and then it gives me some info that I need to type into the terminal. So, if I am right about the need for drivers, how do I enable universe and multiverse repositories, and I feel dumb for asking, but i've googled this without success... how do i bring up the terminal from the login screen?

---

### Post by Sutekh on 2006-03-21
First you should try the command
```
sudo dpkg-reconfigure xserver-xorg
``` to setup up the X server.  Work your way through the process,  when unsure go with the recommended / default option.

You should be able to at least get X windows working before needing NVIDIA drivers, which you can look at later.

---

### Post by chuckyp on 2006-03-21
Well if you hit ctrl+alt+f1  it will bring up a virtual console and hitting ctrl+alt+f7 will bring you back into xwindows.  f1-f6 should be virtual consoles. f7 is window manager.
Once there, edit your sources.list "sudo nano /etc/apt/sources.list"  uncomment the lines with multiverse and universe by removing the # in the front.  You do not need the once that have deb-src.  Press ctrl+x to exit it will prompt you to save the file.
Then "sudo apt-get update"  it will see which packages are currently availible.  Then "sudo apt-get install nvidia-glx"  I believe you will also need linux-modules-restricted-`uname -r` if it doesn't install them.  "sudo apt-get install linux-modules-restricted-`uname -r`"
After everything is installed then "sudo /etc/init.d/gdm restart"  that will restart the window manager.

---

