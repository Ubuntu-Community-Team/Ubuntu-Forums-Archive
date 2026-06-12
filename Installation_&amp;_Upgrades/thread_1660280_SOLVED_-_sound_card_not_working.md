---
title: "SOLVED - sound card not working"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by cdbg on 2011-01-05
Hi all,

I solved a small problem about my sound card ,after installing a brand new xubuntu 10.10 ,by myself, anyway here I send you what was supposed to be my email to the ubuntu forum, it's pretty simple but maybe it can help someone ....[COLOR=Blue] solution follows[/COLOR]

-----------------------------------------------------------------------------------------

Hi all,


after installing xubuntu 10.10 my sound card is not working, no youtube nor CD roms etc ...

it's an embedded sound card  and is detected as [COLOR=Blue]sis si7020 alsa mixer[/COLOR]

it seems like the configuration is not ok as I cannot listen anything through my speakers (which are working), and I don't have any other sound card installed.


checking the configuration, the line-in has volume, as the Cd and Aux

here you have an lspci

--------------------------------------------------------------------------------------------------------------------------

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 741/741GX/M741 Host (rev 03)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:0b.0 Network controller: RaLink RT2561/RT61 rev B 802.11g
01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (rev 01)
01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] (Secondary) (rev 01)



Thanks 
--------------------------------------------------------------------------------------

 I solved this just going to the audio configuration and changing the default option to [playback internal audio analog stereo pulseaudio mixer],

click on  SELECT CONTROLS
tick on MASTER
then increase the volume


Best Regards

---

