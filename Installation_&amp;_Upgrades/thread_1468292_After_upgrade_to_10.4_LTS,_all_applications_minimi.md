---
title: "After upgrade to 10.4 LTS, all applications minimize"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by kb7qdi on 2010-05-01
I just upgraded my netbook from 9.10 to 10.4 LTS.  The installation seemed to work just fine, and after the reboot all things came up as expected.

However, when I click on a program, it will appear, then immediately minimize in the upper-left corner.  If I click on it, it will reappear then go back within a second.

I also noticed that if I move to a different area and run another application within there (OpenOffice for example), again the application will appear and minimize, but also the desktop is moved back to the Favorites.

It's very flustrating, as my mouse skills are not as good as the PC minimizing.

The only thing that I noticed (may or not be relevant) was when I finally got it good enough to log off, a quick popup showed up about an Unknown program unable to end.

Has anyone else experienced this.  Is there something I can do to resolve this, or am I stuck on building 10.4 from scratch?

Thanks, Dean

---

### Post by zteifel on 2010-05-01
I'm experiencing the exact same thing after updating from 9.10 to 10.04 with mine Acer EEE pc.

---

### Post by bravid on 2010-05-01
Same thing here. I think they are getting pushed to the background behind the launcher. You can switch to Gnome at the login screen until this gets fixed.

---

### Post by stephendowd on 2010-05-02
Same problem with my Acer Aspire One. It is driving me mad. ](*,) I've been trying to play around with Compiz Config Settings Manager (which isn't easy when you have a second before the application minimises) to no avail. When I switch to Gnome/Gnome failsafe I just get a black screen and I have to reboot using the power on button. I would caution anyone with a netbook not to upgrade until this is sorted out. Lucid Lynx is currently a jinx! :evil:

---

### Post by cryptic73 on 2010-05-02
I ran into the same problem. Somehow the netbook maximization-thingy gets confused when there is not GLX-support in the x server. And GLX didn't work because a nvidia-specific glx-driver got loaded for my intel graphics.

In short, I solved it by removing all nvidia drivers via synaptic in the 'netbook 2d mode'

---

### Post by ehaus on 2010-05-03
I am having the same issue.  It's an Asus EEE PC.

---

### Post by ehaus on 2010-05-03
cryptic73 - thanks.  Uninstalling the nvidia packages solved the issue.

---

### Post by GusTheSadGeek on 2010-05-04
I fixed this on my Acer Aspire One :-


Ctr-Alt-F2   - to get a command shell
login
sudo apt-get remove nvidia*
sudo reboot

---

### Post by sleepingdragon on 2010-05-07
Removing nvidia* did nothing for me - exactly the same problem as before.

---

### Post by flatfour on 2010-05-09
Same problem here on a Toshiba Tecra 9100, removing the Nvidia apps also hasn't helped...

can't even get my wireless key typed in! grrr!

---

### Post by SteveTPearce on 2010-06-02
Thanks also, cryptic73. Removing the nvidia packages also fixed this issue with my EeePC 1008HA.
Have to say, though, it's not the standard of quality control I'm used to from Ubuntu. I actually had to resort to *Windows* in order to find this fix. Can you imagine..?

---

