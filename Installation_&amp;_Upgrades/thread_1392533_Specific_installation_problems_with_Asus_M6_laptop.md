---
title: "Specific installation problems with Asus M6 laptop"
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by bacchusmarsh on 2010-01-28
Ok. So to begin with i downloaded 9.10 iso and used USB creator on a eeepc to make a usb startup in order to install onto an Asus M6.
The installation went well until i rebooted and the OS would not load ([see this explanation and solution if you want to]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search")). Then i found karmic (9.10) had all these internet connection problems and mine was that the wireless and auto etho both connected but i could not access any webpages, or recieve any updates etc... 
so i gave up on karmic and managed (after much stuffing around with incomplete downloads etc) to download and install 9.04 with the same usb.
Then the Asus wouldnt recognise the 9.04 live on the usb, it wouldn't boot (several more hours of stuffing around pass...) but i found by changing the hardrive setting in the Bios (not the boot order, that didn't work) so that the usb was first and the main hard drive was second, it booted! yeah!
I had chose 9.04 to install because i used to run it on my old laptop and it was great, and i knew there weren't any internet problems, but... when i tried to install i came up with this error:

Ubuntu is running in Low graphics mode.
error: update configuration to solve

(EE) intel(0): output LVDS enabled but has no modes
(EE) intel(0): no valid modes
(EE) screen(s) found, but none have usable configuration.

Sure enough when the install was completed ubuntu comes up with this message on boot and i have to select running low graphics mode. This did not happen with 9.10 (karmic)

Now if any body could help me solve either the internet problem specific to those symptoms (i can't find it in the forums) in 9.10
or
the graphics/display problem in 9.04, then i would be eternally grateful.

i found this linux forum [here]("http://www.openlaptops.org/forum/search.php?mode=results") specific to asus m6 series but it is really old and there is no mention of ubuntu beyond 5.04

---

