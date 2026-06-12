---
title: "How did your upgrade to feisty go?"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by thelocust on 2007-05-07
I'm looking to upgrade to feisty and I was just wondering what the general experience was. Especially with Kubuntu since I'm running KDE. Thanks.

---

### Post by akudewan on 2007-05-07
I had to upgrade from the commandline, since the Upgrade tool on the DVD was crashing. And samba broke after the upgrade (which I managed to fix quite easily).

Apart from this, the upgrade process was nice and smooth. Much better than the previous release :)

---

### Post by p.n on 2007-05-07
I thouroghly distroyed my system and did not have the stomach to try and get it up and running so I did a complete new install....

---

### Post by megamania on 2007-05-07
Everything went fine. I upgraded from Edgy to one of the Feisty betas (around one month before final).

I just realized I had to reinstall NFS for some reason though, so I voted for the "tweak" option.

---

### Post by hartz on 2007-05-07
My upgrade from the internet worked perfect (I used the command [COLOR="Red"]**sudo update-manager -d**[/COLOR]).  

It seems that much of my non-default software also got upgraded, for a total download of about 1.6 GB.

Note: If you are using legacy drivers be sure to have the update(s) on hand before you start.

I had one issue but I expected it.  My graphics card has got two GPUs, but Ubuntu (and all other Distros that I have tried to date) picks the first one incorrectly.  This leaves me with a black screen in all LiveCDs, GUI-installers, and also on first boot after installing Linux via text mode.

The fix for this is to edit the /etc/X11/xorg.conf file, and change the device's  BusID entry to point to the correct GPU after the instalation completed.  After changing this file a simple [COLOR="Red"]**sudo /etc/init.d/gdm restart**[/COLOR] command gets X-windows to work once more.

Because I expected it I backed up my xorg.conf file (heavily customized) before I started the upgrade.

I have used the online upgrade process from 6.06 to 6.10, then from 6.10 to 7.04, without ever needing to re-install anything, except for my legacy drivers.  And this is despite using custom compiled kernels in between, which goes to show just how good the upgrade process is.

Note:  The upgrade process can sometimes downgrade your kernel to an older release, if you are running a custom compiled kernel, but this is not something that most users would have to worry about.

---

### Post by akudewan on 2007-05-07
> **hartz3 said:**
> My upgrade from the internet worked perfect (I used the command [COLOR="Red"]**sudo update-manager -d**[/COLOR]).  

It seems that much of my non-default software also got upgraded, for a total download of about 1.6 GB.

Note: If you are using legacy drivers be sure to have the update(s) on hand before you start.

I had one issue but I expected it.  My graphics card has got two GPUs, but Ubuntu (and all other Distros that I have tried to date) picks the first one incorrectly.  This leaves me with a black screen in all LiveCDs, GUI-installers, and also on first boot after installing Linux via text mode.

The fix for this is to edit the /etc/X11/xorg.conf file, and change the device's  BusID entry to point to the correct GPU after the instalation completed.  After changing this file a simple [COLOR="Red"]**sudo /etc/init.d/gdm restart**[/COLOR] command gets X-windows to work once more.

Because I expected it I backed up my xorg.conf file (heavily customized) before I started the upgrade.

I have used the online upgrade process from 6.06 to 6.10, then from 6.10 to 7.04, without ever needing to re-install anything, except for my legacy drivers.  And this is despite using custom compiled kernels in between, which goes to show just how good the upgrade process is.

Note:  The upgrade process can sometimes downgrade your kernel to an older release, if you are running a custom compiled kernel, but this is not something that most users would have to worry about.

Wow....you have like...a Dual core graphics card??!!! Thats so COOL!!! :shock:

---

### Post by hartz on 2007-05-08
The card is the Gigabyte GV-3D1. - I.e. the card reviewed [here]("http://www.pcstats.com/articleview.cfm?articleID=1749"): 

thank you, yes it is cool enough, SLI even works with the nVidia legacy drivers, though I don't play enough games to use it ever.

---

### Post by starcraft.man on 2007-05-08
My upgrade was kinda weird. I tried to do the upgrade via update manager and well it refused to boot up after that, I then did a clean install and it worked well out of the box, just a few problems with beryl and my torrent manager that I fixed fast. So I'd say upgrade, unless you really have no time for minor tweaks.

---

### Post by Sunflower1970 on 2007-05-08
The upgrades went perfectly here on all my computers....but I had a problem on my laptop with suspend/hibernate. Had to revert back to Edgy so that would work again. :(

---

### Post by mjgumbley on 2007-05-08
It hung my system completely during installation, leaving me with a non-booting system that resisted all attempts at repair. Single-user mode now hangs. It'll need a fresh install.

Given the standard of the Feisty upgrade, I feel that it needs to be more prominent that non-LTS releases are effectively betas.

---

### Post by thelocust on 2007-05-14
Cool, Thanks for all the inputs turns out I just bought a brand spankin new computer so I'll just do a fresh install.

---

### Post by The Muttster on 2007-05-14
Fairly painless. 

Removed the nVidia driver beforehand, the upgrade removed Apache plus a couple of others I didn't recognise. PHP4 looks to be deprecated now so I had to tidy up Squirrelmail and PHPMyAdmin after reinstalling Apache.

---

### Post by otchie1 on 2007-05-14
> **hartz3 said:**
> My upgrade from the internet worked perfect (I used the command [COLOR="Red"]**sudo update-manager -d**[/COLOR]).  

It seems that much of my non-default software also got upgraded, for a total download of about 1.6 GB.

Note: If you are using legacy drivers be sure to have the update(s) on hand before you start.

I had one issue but I expected it.  My graphics card has got two GPUs, but Ubuntu (and all other Distros that I have tried to date) picks the first one incorrectly.  This leaves me with a black screen in all LiveCDs, GUI-installers, and also on first boot after installing Linux via text mode.

The fix for this is to edit the /etc/X11/xorg.conf file, and change the device's  BusID entry to point to the correct GPU after the instalation completed.  After changing this file a simple [COLOR="Red"]**sudo /etc/init.d/gdm restart**[/COLOR] command gets X-windows to work once more.

Because I expected it I backed up my xorg.conf file (heavily customized) before I started the upgrade.


just to expand on that for non ubers.

lspci will reveal the BUSIDs  of your GPU. With a two GPU setup change the BUSID in /etc/X11/xorg.conf to the higher number (7:0:0 in my case).

Would be nice to see a dynamic xorg.conf one day.

2 x 7600 in my case and SLi seems to work fine :-)

---

### Post by etcpool on 2007-05-14
i do fresh install, and it's such a good since then..

---

