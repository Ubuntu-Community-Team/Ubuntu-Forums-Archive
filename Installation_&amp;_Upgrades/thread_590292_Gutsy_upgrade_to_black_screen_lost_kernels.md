---
title: "Gutsy upgrade to black screen /lost kernels"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by ocian on 2007-10-24
I recently upgraded to gutsy from feisty on my laptop with ATI mobility radeon 9700.

After install, I rebooted but upon reboot I get to the Ubuntu Splash progress page (with the progress bar) but then a blank black screen where I would normally login. No cursor, nothing. It almost looks like my screen shuts off.

I tried searching around for people with similar problems and I'm thinking it might be something to do with my xorg.conf or something that's making my screen undetected. 

On top of that, it seems my previous kernels are no longer listed in my grub so only option is using terminal. 

I'm not so hot with terminal so if anyone could direct me how to fix this or what might be the problem, I greatly appreciate it

---

### Post by jsnelli2 on 2007-10-24
Yeah...I've got a similar problem.  I updated via the alternate cd from Feisty.  When it got done and wanted to reboot it showed the splash screen and then went into terminal saying that there is no previous image saved.  I also am not keen on using the terminal...Any ideas?  I really don't want to do a clean install.

---

### Post by ocian on 2007-10-25
Okay I fixed it pretty much. Don't know about the lost kernels but im assuming upgrading to 7.10 auto deletes 7.04....

anyway in recovery terminal i reconfigured my xserver and that was enough to get logged on. then everything was all laggy and choppy so I enabled the restricted drivers for ati and everything seems to be running smoothly (for the most part). I consider this solved

---

