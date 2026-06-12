---
title: "S3 Savage Video card"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by eros82ca on 2007-07-01
I know that 3d acceleration in available in previous versions of Ubuntu, but there are dozens of threads for solving this problem in previous versions, but not feisty (ubuntu studio).  

Currently I have VT8375 [ProSavage8 KM266/KL266] and I know that it is capable of the 3d desktop environment, however, that option is not available.  Nor is my computer reporting any restricted drivers, etc, etc.  

So does anyone know any way that I can make this work?

---

### Post by bapoumba on 2007-07-01
```
~$ lspci | grep Savage
00:00.0 Host bridge: VIA Technologies, Inc. VT8605 [ProSavage PM133]
01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02)
```
I have an old Savage video card.

```
~$ aptitude search restricted
<sniped out non-installed or irrelevant packages>
i A restricted-manager              - manage non-free hardware drivers 
```
This is the only restricted package installed.

I had 3D rendering installed running:
```
sudo dpkg-reconfigure xserver-xorg
```
Logout from your session, hit CTRL-ALT-F2 to log in a non-graphic session. Run the dpkg-reconfigure command. Keep the default answers when you do not know.At some point, it should pick up the savage driver. To go through the options, use <tab>, to select an option usse <space>.
When you are through, CTRL-ALT-F7 will return you to the graphic session. Log back in. You should be set up.

Look at your xorg.conf, the Device section should look like this, (adapted for your own video card):
```
cat /etc/X11/xorg.conf
Section "Device"
        Identifier      "S3 Inc. 86C380 [ProSavageDDR K4M266]"
        Driver          "savage"
        BusID           "PCI:1:0:0"
```

---

### Post by eros82ca on 2007-07-03
Thank you so much, and I can get my glxinfo now rather than having nothing, but rendering still isn't operating yet.  Still trying to figure out why......

---

### Post by bapoumba on 2007-07-03
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88905) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Please look at the bug report, if it applies to your video card.

```
~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2

```

---

