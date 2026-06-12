---
title: "Driver update went bad"
date: 2011-11-12
forum: Installation &amp; Upgrades
---

### Post by Agent26 on 2011-11-12
Hi there all, 
I am a linux noob, just over from windows.
I am not a expert computer user but managed windows fine and considered myself to be fairly competent at whatever was thrown at me.
 
Just a quick apology if this is in the wrong palce.
 
Anyhow, I recently installed Xubuntu on my old desktop pc and have been having problems, I tried to update the drivers to the reccomended geoforce but instead of changing to the correct driver it uninstalled the existing driver and failed.
 
Everything now is huge but my problem is half of the windows are of screen. 
 
What can i do???
 
Please can a advanced user help me as i'm stuck. 
Thankyou

---

### Post by AlexDudko on 2011-11-12
Install your deleted driver back.
> apt-get install your_old_working_driver_name
reboot

---

### Post by Agent26 on 2011-11-12
Hi and thanks for that but i am unable to see anything below halfway of the screen so I cant select things as I simply cant see them.
 
I tried to install the drivers of of a memory stick but when it opens I am unable to see even half of the window. minimizing ect wont reveal anymore either.
 
Is there some other way?

---

### Post by AlexDudko on 2011-11-12
> ctrl+alt+f1
will give you cli (command line interface).
Log in as root and run:
> dpkg -e updated_package_name.deb
After that install the default Ubuntu driver package as it was mentioned in my previous post.

---

### Post by AlexDudko on 2011-11-12
Your package name should be > xserver-xorg-video-nouveau
If you haven't got Internet connection then simply download it [here]("http://packages.ubuntu.com/oneiric/xserver-xorg-video-nouveau") on another machine and install it with 
dpkg command.

---

### Post by Agent26 on 2011-11-12
Hi Alex thanks again.
 
Sorry to be a bigtime noob but when I get to the CLI login screen it asks for Ubuntu login, I type root and it then asks for a password? My user pasword doesn't work.

---

### Post by AlexDudko on 2011-11-12
Try to log in with your account name and then acquire root privileges using sudo before command.

---

### Post by Agent26 on 2011-11-19
Thankyou and sorry for the late reply, alls solved now.
Thankyou also for giving me an idea of what terminal is.

---

