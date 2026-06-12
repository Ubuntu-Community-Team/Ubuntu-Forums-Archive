---
title: "kubuntu hangs after upgrade to gutsy on splash-screen"
date: 2007-12-09
forum: Installation &amp; Upgrades
---

### Post by odinb on 2007-12-09
Hi!

Upgraded my father-in-laws laptop from Feisty to gutsy earlier today, and the wizard/installer hung with a message about some x11-common issue.

I ran the upgrade over a remote desktop connection, since he is in another country than me (I am in the US, he is in Sweden).

Checked the sources-list, and it had the gutsy repositories, so I thought, what the heck, lets do it manually!

Ran
sudo apt-get upgrade -f (would not run without the forcing)
sudo dpkg --configure -a (said I had to)
sudo apt-get dist-upgrade

reran all 3 commands above, and it seemed like it had done its job, so I went ahead and told him to do a reboot.

It now hangs at the splashscreen (the blue cog) about 3/4 up on the progressbar, and will only boot in recovery-mode after several tries.

Have tried reinstalling x11-common:
sudo apt-get install x11-common --reinstall

Have tried reconfiguring it:
sudo dpkg-reconfigure usplash

Have tried reconfiguring usplash:
sudo dpkg-reconfigure usplash

None helped.

What can I do next, or is it hosed?

---

