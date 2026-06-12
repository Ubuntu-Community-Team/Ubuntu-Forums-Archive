---
title: "Hardy broke all my games!"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by ubu-wan-n00bie on 2008-05-17
Hi Guys, 

Before I detail my problem, my PC is a pre-built system (Puget) consisting of an Asus A8N-SLI mainboard, an Athlon 3500+ x64, 1Gb of corsair VS DDR2, an 80GB WD SATA hdd, a BFG Tech 7600GS video card, as well as an Neovo F-419 19" LCD monitor which I ran at its native resolution (1280 x 1024 and 75hz) and logitech PS/2 mice & keyboard. About 6 weeks ago, I flipped the switch, hopefully forever, and dumped windows for Ubu 7.10. After a brief learning curve, all was well and virtually everything ran absolutely perfectly. I play ioquake3, World of Padman, and the postal 2 series of games. OpenGL worked perfectly in these games with Nvidia's 169.12 drivers and all was well until I tried to upgrade to 8.04 LTS.

Firstly, I tried upgrading from GG. The upgrade process ran error free and all seemed to be well. As per the Envy NG instructions, I removed the nvidia 169.12 drivers prior to the upgrade and replaced them with the mesa drivers. I did notice that HH defauled to 1280 x 1024 at 50Hz. I ran Alberto Milone's excellent Envy NG script to replace the 169.12 nvidia driver, rebooted, ran the xconfiguration thingie ***as root***, changed the resolution to 1280 x 1024 by 75hz and saved the xconfig file (/etc/x11/xorg.conf). No other changes were made at this time such as anti-aliasing or anisotropic filtering. All was well. 

That is, until I tried to run ioquake3 at 1280 x 1024 fullscreen. The game displayed itself in a maximized desktop window and the mouse pointer froze in the upper left hand corner of the display configuration screen. The game itself was *not* unresponsive, as i was still able to use the keyboard to change configuration settings. Changing the game resolution to any other setting unfroze the mouse and returned the display to fullscreen. World of Padman, also a Q3 engine game, based on the ioquake3 source port, exhibited the same behavior. Later I found that Postal 2 had the same problem. Playing the game at another resolution is not a viable option as on the LCD running the game at other resolutions make it look like hell and I like the eye candy

All other aspects of video performance seemed ok (GL screen savers, etc....) and I noticed no other problems with Ubuntu. However, inasmuch as I love my quake3, I put 7.1 back and, as before, everything seemed to run flawlessly.

After a time, influenced by many rave reviews and enthusiastic endorsements, I did a *CLEAN* install of HH 8.04 Ubu. By clean, I mean I completely cleaned the hdd of partitions with free DOS including fdisk /mbr and installed Linux from the CD. From the vanilla desktop I installed the packages I like (nothing special, banshee, easytag, xchm etc.....) and updated everything. The system was ,at this point, as stable as I knew how to make it. I ran Envy NG and installed the nvidia 169.12 drivers, edited the xorg.conf to give me 1280 x 1024 x 75hz, rebooted, checked GL rendering and ,when I was satisfied everything was everything, installed ioquake3.

Again, to my chagrin, when I tried to run the game at 1280 x 1024, the stupid maximized window appeared again and the stupid mouse froze in the upper left hand corner of the screen. 

At this point, I am at a loss as to how to proceed. everything else works great. 8.04 runs great in every other regard and I really really want to make this work for me. I can't understand why a driver works with 1 verion of ubuntu but not another. 

I appreciate any and all help. TIA.

Ray "Ray Ray" Davis

---

