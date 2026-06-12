---
title: "I'm stupid - how do I get NVidia drivers to make my screen work?"
date: 2008-05-18
forum: Installation &amp; Upgrades
---

### Post by Fzang on 2008-05-18
At the section "hardware drivers" I have a device called "nvidia_new" which is my graphics card, which I need the correct drivers for...

Now how do I do that..?

---

### Post by Jungle-Cat on 2008-05-18
I'm not sure about 8.04, since I'm still trying to install it... but in 7.10, you go to "Restricted Drivers Manager".

---

### Post by tommcd on 2008-05-18
> **Fzang said:**
> At the section "hardware drivers" I have a device called "nvidia_new" which is my graphics card, which I need the correct drivers for...

Now how do I do that..?

What nvidia card do you have?   Instead of using the restricted drivers manager (I just don't trust it to install the right driver) open up synaptic package manager and install the correct driver. See this:
[https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA?highlight=%28new%29%7C%28nvidia%29%7C%28glx%29](https://help.ubuntu.com/community/RestrictedDrivers/NVIDIA?highlight=%28new%29%7C%28nvidia%29%7C%28glx%29)
So anything above Gforce 5 series is nvidia-glx-new.
After the driver installs open a terminal (applications > accessories > terminal) and run "sudo nvidia-xconfig". Then restart X with ctrl + alt + backspace (or reboot) and you should get the nvidia logo.
Back up your xorg.conf first though, like this:
"sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak". Do this in the terminal.

Write back if you need more help.

---

### Post by Malta paul on 2008-05-18
If you still have problems why not install 'EnvyNG' (for 8-04) its very good and will find the latest driver and install for you.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
Hope is is of help.

---

### Post by Fzang on 2008-05-18
Just a note, my connection doesn't work either, so I can't use any online updates or such

---

