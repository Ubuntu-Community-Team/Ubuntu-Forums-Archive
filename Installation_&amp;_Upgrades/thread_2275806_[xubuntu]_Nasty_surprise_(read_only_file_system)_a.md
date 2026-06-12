---
title: "[xubuntu] Nasty surprise (read only file system) after 15.04 Upgrade + Solution"
date: 2015-04-28
forum: Installation &amp; Upgrades
---

### Post by igor39 on 2015-04-28
Hi,

just managed to solve a nasty surprise I had after upgrading my Xubuntu from 14.10 to 15.04.

Supposedly smooth upgrade (no errors reported) but after the restart my system ended up in low res textmode with read-only filesystem... Recovery mode did not help with anything, live USB booted Xubuntu normally (so no HW issues).

I managed to solve it using hint from this thread: [http://ubuntuforums.org/showthread.php?t=2275099](http://ubuntuforums.org/showthread.php?t=2275099)

Indeed, the switch from upstart to systemd is apparently not bulletproof and passing init=/sbin/upstart to kernel did help to have my system back, intact.

I've no idea where to submit a bug with upgrade procedure (I assume breaking it into state beyond repair capabilities of a regular joe was not a "feature") + report fact that this [https://wiki.ubuntu.com/SystemdForUpstartUsers](https://wiki.ubuntu.com/SystemdForUpstartUsers) document is inaccurate ('In grub, select "Advanced options for Ubuntu", where you will find an "Ubuntu, with Linux ... (upstart)" entry.' => I had no such option after upgrade...), but maybe someone who does know will or at least this post will help other poor souls with similar problem.

---

### Post by grahammechanical on 2015-04-28
That wiki page is accurate if a person was using Vivid Vervet (15.04) during the development cycle.

> If you are running Ubuntu vivid (15.04), you can easily switch between  upstart and systemd at will since both packages are installed at  present. As of March 9 2015, vivid was changed to use systemd by  default, before that upstart was the default.

I was running Vivid Vervet and at the beginning of March my system had defaulted to upstart with systemd as an Advanced option. A new install of the daily ISO image defaulted to systemd with upstart as an Advanced option. Then as the release date of 15.04 neared the upstart Advance option no longer appeared in the daily images. 

Regards.

---

### Post by igor39 on 2015-04-29
Shame I did not. It would have caused me some headache...

---

