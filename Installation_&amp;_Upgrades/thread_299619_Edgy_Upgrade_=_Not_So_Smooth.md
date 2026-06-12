---
title: "Edgy Upgrade = Not So Smooth"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by timbobsteve on 2006-11-14
Hi All,

Just thought I would write to tell you all about the terrible upgrade I just went through with dapper->edgy. I am running an ibook G3 900Mhz running Ubuntu PPC Dapper. I wanted to upgrade and decided to use the dist-upgrade method. Firstly a lot of the apt-get update's were failing due to my mirrors timing out. This was fixed by changing the server from http:// to [ftp://.](ftp://.)

The second problem I ran into was the fact that the upgrade requires you have ubuntu-desktop meta-package installed. This was a pain becuase I had already removed OpenOffice.org from my system, thus breaking ubuntu-desktop. My connection is rather slow, so downloading all the updates would be painful, so I thought I would just use my Dapper PPC CD to install the ubuntu-desktop meta-package from the CD. As it turns out the Dapper CD doesn't contain a meta package for ubuntu-desktop. I thought I would at least install the dependancies for ubuntu-desktop (oppenoffice.org), but they weren't on the CD either (funny though, they were installed as default :/ ). So in the end I had to sit through the extra downloads before even beginning the upgrade to Edgy.

After it was all done I started the upgrade. 2 days later I was ready to reboot (I told you it was a slow connection). I rebooted my system and chose linux from the yaboot menu. The first thing I noticed was that there was no Splash Screen. Strange. Secondly X failed to start. I had to switch to a VTerm and troubleshoot. An hour later it turned out that xorg had not been updated and, infact, it had been half-uninstalled. I had to apt-get xserver-xorg and reboot before GDM would even display. I managed to do that and reconfigure GDM (which had lost all my settings) and my desktop (which had also lost all my settings).

One strange thing that IS working, is gtkpbbuttons. I original posted about GTKPBButtons failing to load themes when added to the Gnome Sessions startup list. Now it seems that it IS loading.

I still have no splash screen, dispite trying all the suggestions I could find on the forums (dpkg-reconfigure, apt-get install usplash-theme-ubuntu, reconfigure yaboot). If anyone knows how to fix the dissappearing usplash problem can you please let me know. Dmesg is telling me that frambuffer has loaded correctly (radeonfb), so usplash should be working.

All in all, the upgrade to edgy was a pain in the a$$. Its ok though, from what I hear Ubuntu is looking to drop all but LTS version support for PPC. Ouch!

-Timbobsteve

EDIT: Also my network has stopped working after reboot. I have to manually restart networking via "/etc/init.d/network restart" :(

---

