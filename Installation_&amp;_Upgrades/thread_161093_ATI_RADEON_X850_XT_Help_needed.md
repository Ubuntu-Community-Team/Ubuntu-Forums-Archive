---
title: "ATI RADEON X850 XT Help needed"
date: 2006-04-16
forum: Installation &amp; Upgrades
---

### Post by general_error on 2006-04-16
I have a ATI x850 and can't get the ATI proprietary drivers ( Version 8.24.8) to recognize my card.

# lspci |grep ATI
0000:01:00.0 VGA compatible controller: ATI Technologies Inc: Unknown device 4b49
0000:01:00.1 Display controller: ATI Technologies Inc: Unknown device 4b69

# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=5.10
DISTRIB_CODENAME=breezy
DISTRIB_DESCRIPTION="Ubuntu (The Breezy Badger Release)"

# uname -a
Linux jackal 2.6.12-10-386 #1 Sat Mar 11 16:13:17 UTC 2006 i686 GNU/Linux

# glxinfo |grep direct
direct rendering: No
OpenGL renderer string: Mesa GLX Indirect

# fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.2.1)

According to [http://gentoo-wiki.com/HOWTO_X850XT_ATI_Drivers]("http://gentoo-wiki.com/HOWTO_X850XT_ATI_Drivers") support for this card was added as of the 8.23.7 driver.

Someone on another forum posted "All you have to do is install the xorg-driver-fglrx package, but you need the one that is dapper, not breezy."

So how do I just install this package from dapper to get it to work?  Do I need to install the dapper kernel?  How do I get packages just out of dapper?  Should I reimage my box with dapper?

I just want the native ATI driver to work.

---

### Post by cilynx on 2006-04-17
The Wiki is your frind...

[https://wiki.ubuntu.com/BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI")

---

