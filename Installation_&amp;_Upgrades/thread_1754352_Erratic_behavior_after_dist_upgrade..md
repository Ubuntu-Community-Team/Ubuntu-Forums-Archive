---
title: "Erratic behavior after dist upgrade."
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by the_siggy on 2011-05-09
Hi to all, I hope this is the right place to post this. I've recently upgraded one of my desktops to Ubuntu 11.04 from 10.10 version. This is my daughters desktop so, other that a few firewall rules, it was all configured @ defaults for ubuntu 10.10
After the upgrade (which went smoothly, btw) I've been having this weird issues with the video: each time i reboot the console & X resolutions change. The console should be @1024X768 and X @1280X1024. But (i.e.) in the first boot the console gets set to 1280X1024 (by console I'm saying all that its in the framebuffer prior to X server is started) and gdm starts @1024X768. In the next reboot console gets set @ 640X480 and gdm start @1280X1024. Sometimes i get weird combinations like 800X600 + 1152X864. My hardware details are [here.]("http://paste.ubuntu.com/605545/")
The software versions are = as any default up to date Ubuntu 11.04 with the addition of google chrome beta.

Any thoughts?

---

