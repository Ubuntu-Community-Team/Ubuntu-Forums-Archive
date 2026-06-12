---
title: "GUI partition tool for console?"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by 3DLover on 2006-11-29
I'm looking for a GUI tool for managing partitions in a console.  I have installed Ubuntu Server, so I don't have X Windows at all.  fdisk and sfdisk are entirely command line.  parted is slightly better, but it's not really a GUI.  cfdisk has somewhat of a GUI, but it only works on one disk at a time, and there's no advanced options like configuring LVM or RAID.  Just partitioning.

I love the partition tool that is available during the OS install procedure.  You can partition, configure RAID's and LMV sets.  It can format the partitions with several different file systems, it can set labels and it can insert your volumes into your fstab.  Is this tool available as a stand-alone program?  I can't find it anywhere.  I think it's called parted_server, but I can't find much information about where to get it.

In the past, I have run the Ubuntu install procedure just to use the partition manager that comes with it.  (canceling the install after making my partition edits)

Anyone help me on this?  Thanks

-Ray

---

### Post by KingBahamut on 2006-11-30
sudo apt-get install gparted
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by 3DLover on 2006-11-30
gparted is probably a fine tool.  But not for me.

```

# >sudu apt-get install gparted
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  appres beforelight bitmap editres fontconfig freeglut3 fstobdf gconf2 gconf2-common gksu gnome-keyring iceauth
  ico imake laptop-detect libatk1.0-0 libcairo2 libdmx1 libdrm2 libexpat1 libfontconfig1 libfontenc1 libfs6
  libgconf2-4 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libglib2.0-0 libglibmm-2.4-1c2a libglu1-mesa
  libgnome-keyring0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a libice6 libidl0 libjpeg62
  liborbit2 libpango1.0-0 libpango1.0-common libsm6 libstartup-notification0 libtiff4 libx11-6 libxau6 libxaw7
  libxcursor1 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxmuu1 libxpm4 libxrandr2
  libxrender1 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 listres makedepend
  mcpp mesa-utils oclock sessreg smproxy ttf-bitstream-vera ttf-freefont ucf viewres x11-common x11perf xauth
  xbase-clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd
  xfonts-utils xfontsel xgamma xgc xhost xinit xkbutils xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman
  xmessage xmodmap xmore xpmutils xprop xrandr xrdb xrefresh xrgb xset xsetmode xsetpointer xsetroot xsm xstdcmap
  xtrap xutils xvidtune xvinfo xwd xwininfo xwud
Suggested packages:
  ttf-kochi-gothic ttf-kochi-mincho ttf-thryomanes ttf-baekmuk ttf-arphic-gbsn00lp ttf-arphic-bsmi00lp
  ttf-arphic-gkai00mp ttf-arphic-bkai00mp
Recommended packages:
  ntfsprogs hfsutils libatk1.0-data libglib2.0-data hicolor-icon-theme x-ttcidfont-conf debconf-utils
  libgl1-mesa-dri
The following NEW packages will be installed:
  appres beforelight bitmap editres fontconfig freeglut3 fstobdf gconf2 gconf2-common gksu gnome-keyring gparted
  iceauth ico imake laptop-detect libatk1.0-0 libcairo2 libdmx1 libdrm2 libexpat1 libfontconfig1 libfontenc1
  libfs6 libgconf2-4 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa libglib2.0-0 libglibmm-2.4-1c2a libglu1-mesa
  libgnome-keyring0 libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libgtkmm-2.4-1c2a libice6 libidl0 libjpeg62
  liborbit2 libpango1.0-0 libpango1.0-common libsm6 libstartup-notification0 libtiff4 libx11-6 libxau6 libxaw7
  libxcursor1 libxext6 libxfixes3 libxft2 libxi6 libxinerama1 libxkbfile1 libxmu6 libxmuu1 libxpm4 libxrandr2
  libxrender1 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1 libxxf86vm1 listres makedepend
  mcpp mesa-utils oclock sessreg smproxy ttf-bitstream-vera ttf-freefont ucf viewres x11-common x11perf xauth
  xbase-clients xbiff xcalc xclipboard xclock xconsole xcursorgen xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd
  xfonts-utils xfontsel xgamma xgc xhost xinit xkbutils xkill xload xlogo xlsatoms xlsclients xlsfonts xmag xman
  xmessage xmodmap xmore xpmutils xprop xrandr xrdb xrefresh xrgb xset xsetmode xsetpointer xsetroot xsm xstdcmap
  xtrap xutils xvidtune xvinfo xwd xwininfo xwud
0 upgraded, 133 newly installed, 0 to remove and 1 not upgraded.
Need to get 12.2MB of archives.
After unpacking 57.9MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

Install X just to partition a disk?  No thank you.  Not on a Server.  Thanks for the suggestion tho.  Next?

---

### Post by bapoumba on 2006-11-30
Not sure this is exactly what you are looking for, but there is a gparted [liveCD]("http://gparted.sourceforge.net/livecd.php") .
I do not know much about RAID devices, so I cannot tell about that and you have to reboot on a liveCD though. But  it's a very powerfull tool ;)

---

### Post by yota on 2006-11-30
Hi,

if you are searching a text-based tool, but much more user-friendly than fdisk, you can try 'cfdisk'.
It's in the util-linux package, which should be installed by default.

Hope this helps.

---EDIT: oops, sorry, I should have fully read your first post...

---

### Post by 3DLover on 2006-11-30
Thanks, I never bumped into the gparted liveCD in my google quests. I'll look into it.  

I'm just surprised that I can't find the partitioning tool that's used in the install procedure.  I presume it's a wrapper for parted, and all of the individual lvm/raid tools, but why can't I seem to locate a version that can be run after the OS is installed?  I'd love to be able to keep my downtime at a minimum...  just shut down long enough to plug in new disks and then have a curses based GUI to configure the disks while the system is live.

Besides, the server room is noisy as h*ll...  server mgt through SSH from my comfy chair is so much easier.  :)

---

### Post by 3DLover on 2006-11-30
> **yota said:**
> Hi, if you are searching a text-based tool, but much more user-friendly than fdisk, you can try 'cfdisk'.
It's in the util-linux package, which should be installed by default.


Thanks Yota, but I've already found cfdisk.  It's a nice tool for basic partitioning, but it lacks the ability to format the partitions, or any of the advanced raid/lvm configs that I do.

---

