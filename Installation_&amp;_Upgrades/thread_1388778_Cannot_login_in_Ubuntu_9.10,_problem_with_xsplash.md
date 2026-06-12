---
title: "Cannot login in Ubuntu 9.10, problem with xsplash"
date: 2010-01-23
forum: Installation &amp; Upgrades
---

### Post by Hundredfire on 2010-01-23
Hello everyone, I'm totally new to Ubuntu (so please be patient ^^) and encoutered a login problem after installing Ubuntu 9.10.
   So here's the story: I installed Ubuntu 9.10 and latest updates without any problem on my computer (Spirit 178, no graphics card and a 2.7GHz Celeron processor) and my screen resolution is set at 1280x1024. My computer being so lame, I decided to change it to 1024x768. As long as the session is still open, everything is working perfect but on the next reboot, I'm stuck on the logon screen! I type my password then the loading logo appears, then the screen garbles and loading logo again. After a few seconds, I'm back to the logon screen.
xterm session logs in fine.

What I tried and what actually worked:
-logged in as root user and started X via 'startx'. Then deleted $HOME/.config/monitors.xml. I can thus boot as usual user without any problem but screen resolution is back to 1280x1024!
-logged in as root user and started X via 'startx'. Then reinstalled xsplash via synaptic packets manager. I successfully booted as user with 1024x768 resolution twice!! but only twice, then back to the first status (cannot login anymore)
   I noticed that after I reinstalled xsplash, the loading logo is first in 1280x1024, then the screen garbles the same way it does when I can't login, then I'm back to the loading logo but in 1024x768 this time, then I successfully log in.

I'm totally lost as to how to solve this problem and would be grateful to any helping hands!!
Thanks

---

