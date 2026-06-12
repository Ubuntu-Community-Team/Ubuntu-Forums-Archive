---
title: "Mandriva to Ubuntu guidance please"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by Zill on 2005-11-26
I have been using Mandrxxx for a couple of years now and thought it was time to try another distro - so here I am! Currently using Mandriva LE2005 on a couple of PCs connected via an ethernet hub to an ADSL modem router.

I am hoping to get a few tips from you Ubuntu gurus about how to upgrade, and any "gotchas" I should look out for. Specifically:

1) Any ideas on the best way to extract all the relevant hardware info (ethernet, display, sound etc) from my current Mandriva installation which I will need to install Ubuntu?

2) I obviously expect to do a clean install but would like to keep my old /home directories intact. My current disk partitioning is simply /, /home and /swap. Should I keep my existing partitioning unchanged and, if so, how can I tell the Ubuntu installer to do this?

3) I currently use static IP addresses on my LAN but understand that Ubuntu tries to set IP addresses via DHCP during installation. How would I ensure that my static IPs remain unchanged?

4) My current backup procedure is set up via the Mandriva Drakback tool which is, I understand, simply a GUI front end to tar and gzip, running via cron. I use this tool to backup each PCs /home and /etc to the other PC via NFS.
Can anyone advise if there is a similar GUI tool available in Ubuntu, or will I need to manually configure tar, gzip and cron to run my backup routine?

Any info gratefully appreciated.

Many thanks,

Zill

---

### Post by dsjas297 on 2005-11-26
Keeping your home directories intact is very simple. When at the point of installation when you partition your disks, select the partition where your /home directory is. Make sure that the format option is set to "no", (although i'm pretty sure that Ubuntu installation does not format any disks by default), and set its mount point to /home.

For the othr partitions, do partition them and set the moutnpoints as / and /swap.

---

### Post by paddyg on 2005-11-26
as for 2), just remember to backup (if you want to use them at a later stage) and delete your hidden /home files and folders. Old hidden /home files and folders may cause you trouble when ubuntu installs your new home config files and folders. 

As for 3), you can configure your network later---that's what i always do.

---

