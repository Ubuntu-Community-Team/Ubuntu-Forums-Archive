---
title: "Monitor size in 7.04"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by reb68 on 2007-04-22
I upgrade from 7.04 beta to the final 7.04 by downloading and burning the .iso file. .My screen is at 800 x 600. (not exactly but close) I followed the same path I had to use in the beta to change it to 1054 x 825. (The smaller one is unusable as far  as reading) 
I went to monitor administrator mode configure. Brought up my monitor, (Dell D1025TM) and the changed it to 1025x820  When closing I get a window that the X file needs to be updated. go to x file update in boot and click on it. I do this and it will not boot I have ti reinstall. Trying again with out going to x file and I still have to reinstall. I cannot change to the 1025 screen size without I have to reinstall and then I am back at 800 size. (the screen sizes are not exact because I did not write  them down and I did not want to reinstall again to find them for this post.
If this is critical I will get the numbers. 
Thanks for any help

---

### Post by pepsi_max2k on 2007-04-22
1024 * 768?  anyway... what graphics card do you have? if nvidia, you may be able to run "nvidia-settings" from a command line to try and change things. otherwise you may have to edit the /etc/x11/xorg.conf file and add your own resolutions there manually. search google to find out more...

---

### Post by reb68 on 2007-04-22
I am using a Ati Rage card  and the monitor (DellE1025TM) was at 1024 X 768. When I set it in administrater Mode  I get a window "Log out and select restart X-Server from menu Button" When I do this it will not boot up and I have to reinstall from scratch from my ISO cd. at this time it is at 800 X 600. That is not acceptable as the screen is very cramped after the header and footer.
I really hope you have an answer,

---

