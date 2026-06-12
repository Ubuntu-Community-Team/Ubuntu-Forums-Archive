---
title: "[SOLVED] Can't login after update"
date: 2008-02-17
forum: Installation &amp; Upgrades
---

### Post by bretto_40 on 2008-02-17
Hi,

I'm hoping someone can help here and I'll try and include as much information as I can:

I am running Gutsy and everything was working fine. To include the story in depth it was running ok and then in went offline in January (moving house), and recently on the 16th of Feb 08 got it back up and running on line. Everything was running ok as normal; except of course, because it had been off line for so long it had about 150mb of updates to download and install (I will list them shortly).

They downloaded and installed without error and it needed a reboot. I was going out so rather than reboot I just turned it on and figured everything would still be fine when I came back..... WRONG!

When I came back and booted it up it seemed ok until it tried to boot into Ubuntu. I have it setup to automatically logon, which it did, but it got about a quarter of the way through playing the Ubuntu start up music, then went black, and then came back and asked for my login.

This should not happen because I had set it to automatically login. I logged on, but it would just begin the Ubuntu login jingle again, get a little way through, go black, and then come back to the login.

If I want to I can repeat this process indefinitely.

I have Grub set up to use the Generic version of the kernel. I have to do this because I have a quad core processor and Gutsy does not support the quad core under the i386 version (I've gone down this road), and so I boot up in the Generic version as this has full quad core support.

So, I tried booting up with the generic version. Because of my issue with the quad core explained above, I never bothered to properly set up my Nvidia driver properly for the i386 version so it comes up and says that it's in low graphics mode, but I can at least get into it, albeit at a poor resolution and no 3d acceleration.... but that's beside the point.

Before I go on I must mention that I did look on these forums for people having similar issues and found a post by someon who seems to be having the exact same issue (but in KDE) and it was suggested that the current language package causes this issue and posted the following as a solution:
> 
sudo apt-get install language-pack-kde-en=1:7.10+20071120 language-pack-kde-en-base=1:7.10+20071012

I posted and asked if he could provide a Gnome specific version of this solution but in the end I just jumped the gun and tried it with replacing all instances of KDE with Gnome, and it worked in as much as it went through the motions and advised that the latest version of this package was already installed and didn't make any changes.

This did nothing to change the situation.

I then decided to probe further and booted up into the i386 version of the kernel so I could get into the Ubuntu desktop. I then went to Synaptic and got it's history up so I could have a look at the list of packages that it installed that has buggered my Ubuntu, the language package mentioned above is NOT in the list so I don't think that is the problem.

The following is the list of packages that I updated. Somewhere in this list is the cause of my problem!!
______________________________
Commit Log for Sat Feb 16 09:28:39 2008 
 
 
Upgraded the following packages: 
app-install-data-commercial (8.3) to 8.4 
avahi-autoipd (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
avahi-daemon (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
bind9-host (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
cupsys (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
cupsys-bsd (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
cupsys-client (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
cupsys-common (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
deskbar-applet (2.20.0-0ubuntu2) to 2.20.1-0ubuntu1 
dnsutils (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
evolution-data-server (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
evolution-data-server-common (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
firefox (2.0.0.11+2nobinonly-0ubuntu0.7.10) to 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 
firefox-gnome-support (2.0.0.11+2nobinonly-0ubuntu0.7.10) to 2.0.0.12+2nobinonly+2-0ubuntu0.7.10 
flashplugin-nonfree (9.0.48.0.2+really0ubuntu12) to 9.0.48.0.2+really0ubuntu12.2 
ghostscript (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
ghostscript-x (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
gimp (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1 
gimp-data (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1 
gimp-python (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1 
gs-common (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
gs-esp (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
gs-esp-x (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
hpijs (2.7.7+2.7.7.dfsg.1-0ubuntu5) to 2.7.12+2.7.12-0ubuntu2~gutsy1 
hplip (2.7.7.dfsg.1-0ubuntu5) to 2.7.12-0ubuntu2~gutsy1 
hplip-data (2.7.7.dfsg.1-0ubuntu5) to 2.7.12-0ubuntu2~gutsy1 
kdelibs-data (4:3.5.8-0ubuntu3.1) to 4:3.5.8-0ubuntu3.3 
kdelibs4c2a (4:3.5.8-0ubuntu3.1) to 4:3.5.8-0ubuntu3.3 
libavahi-client3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-common-data (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-common3 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-compat-libdnssd1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-core5 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-glib1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libavahi-qt3-1 (0.6.20-2ubuntu3) to 0.6.20-2ubuntu3.2 
libbind9-30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
libcamel1.2-10 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libcupsimage2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
libcupsys2 (1.3.2-1ubuntu7.1) to 1.3.2-1ubuntu7.5 
libdb4.4 (4.4.20-8.1ubuntu3) to 4.4.20-8.1ubuntu3.1 
libdns32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
libebook1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libecal1.2-7 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libedata-book1.2-2 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libedata-cal1.2-6 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libedataserver1.2-9 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libedataserverui1.2-8 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libegroupwise1.2-13 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libexchange-storage1.2-3 (1.12.1-0ubuntu1) to 1.12.1-0ubuntu2 
libgimp2.0 (2.4.0~rc3-1ubuntu7) to 2.4.2-0ubuntu0.7.10.1 
libgs8 (8.61.dfsg.1~svn8187-0ubuntu3.2) to 8.61.dfsg.1~svn8187-0ubuntu3.3 
libisc32 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
libisccc30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
libisccfg30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
liblwres30 (1:9.4.1-P1-3) to 1:9.4.1-P1-3ubuntu1 
libpt-1.10.0 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1 
libpt-plugins-alsa (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1 
libpt-plugins-v4l (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1 
libpt-plugins-v4l2 (1.10.10-0ubuntu2) to 1.10.10-0ubuntu2.1 
libpulse0 (0.9.6-1ubuntu2) to 0.9.6-1ubuntu2.1 
libsnmp-base (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1 
libsnmp10 (5.3.1-6ubuntu2) to 5.3.1-6ubuntu2.1 
libtheora0 (0.0.0.alpha7.dfsg-2ubuntu1) to 1.0~beta2-2~gutsy1 
libxfont1 (1:1.3.0-0ubuntu1) to 1:1.3.0-0ubuntu1.1 
libxml2 (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1 
libxml2-utils (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1 
linux-headers-2.6.22-14 (2.6.22-14.47) to 2.6.22-14.52 
linux-headers-2.6.22-14-386 (2.6.22-14.47) to 2.6.22-14.52 
linux-headers-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.52 
linux-image-2.6.22-14-386 (2.6.22-14.47) to 2.6.22-14.52 
linux-image-2.6.22-14-generic (2.6.22-14.47) to 2.6.22-14.52 
linux-libc-dev (2.6.22-14.47) to 2.6.22-14.52 
linux-source-2.6.22 (2.6.22-14.47) to 2.6.22-14.52 
ntfs-3g (1:1.913-2ubuntu1) to 1:1.1120-1ubuntu2~gutsy1 
openssh-client (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1 
python-libxml2 (2.6.30.dfsg-2ubuntu1) to 2.6.30.dfsg-2ubuntu1.1 
ssh-askpass-gnome (1:4.6p1-5build1) to 1:4.6p1-5ubuntu0.1 
tomboy (0.8.0-1) to 0.8.0-1ubuntu0.1 
xserver-xorg-core (2:1.3.0.0.dfsg-12ubuntu8) to 2:1.3.0.0.dfsg-12ubuntu8.3 
xserver-xorg-dev (2:1.3.0.0.dfsg-12ubuntu8) to 2:1.3.0.0.dfsg-12ubuntu8.3 
xserver-xorg-video-intel (2:2.1.1-0ubuntu9) to 2:2.1.1-0ubuntu9.1 
 
Installed the following packages: 
libntfs-3g16 (1:1.1120-1ubuntu2~gutsy1)
_____________________________________


If anyone can see in the above list where my Ubuntu has gone wrong and a suggested way to fix it that would be awesome! I have heaps of disk space on all partitions so this is not the issue.

If you need me to get more info, or try something in order to help me, please bare in mind that assuming I know how to do something will just result in me asking you how to do it, so if you could include concise instructions that would be great.

Thanks for your time.

---

### Post by bretto_40 on 2008-02-17
OK,

For those who have a similar issue or are interested.

I fixed the issue by following this thread:
[http://ubuntuforums.org/showthread.p...=1#post4161267](http://ubuntuforums.org/showthread.p...=1#post4161267)

I managed to find this one while looking further (I DID look before). Specifically what fixed my issue was re-installing my video drivers.

I run a NVIDIA Geforce 8500GT and it appears that the latest Xorg-core updates can screw the install by removing a symbolic link that is needed.

I followed the usual method of re-installing the driver and during the process it mentioned the following, which it usually doesn't:

File '/usr/lib/xorg/modules/extensions/libglx.so' is not a symbolic link.

So I think this is where the driver re-install fixed it.

I now have full desktop functionality restored as well as Compiz-Fusion.

I hope this helps someone who stumbles across this thread with the same issue. There was mention that this may need to be done again once the xorg-core update is fixed; so hoping a re-install of the diver will fix again if this happens.

Good luck  :)

---

