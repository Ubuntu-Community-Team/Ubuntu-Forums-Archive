---
title: "Removing &amp; cleaning package"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by zkab on 2017-07-29
I downloaded & installed 'sudo dpkg -i unifi-video_3.7.3-Ubuntu16.04_amd64.deb' on my workstation.
Later I installed the package on a server and removed it from my workstation with 'sudo apt purge unifi-video'.
Also cleaned with 'sudo apt-get autoclean && sudo apt-get autoremove && sudo apt-get clean'
But when I 'dpkg -l unifi*' I get following: dpkg-query: no packages found matching unifi-video_3.7.3-Ubuntu16.04_amd64.deb
I thought that purging & cleaning removed every trace of the package ... so how come I get the 'no packages found matching unifi ...'

---

### Post by zkab on 2017-07-29
Solved ... when I deleted 'unifi-video_3.7.3-Ubuntu16.04_amd64.deb' from my download folder then 'dpkg -l unifi*' did not display the message ...

---

