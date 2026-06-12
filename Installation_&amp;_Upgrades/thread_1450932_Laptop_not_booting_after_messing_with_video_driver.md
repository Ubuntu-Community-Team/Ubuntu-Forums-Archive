---
title: "Laptop not booting after messing with video drivers"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by MaxTT on 2010-04-09
Hi,  my teenage son decided to get out sony Vaio Cr laptop working on the tv via an svideo cable. The laptop could not see the tv in display settings so he started trawling the net and adding all sorts of things trying to get it happening. He has installed (I think) some NVidia files (even though the video card is not NVidia). He also added code to the xorg file.

Needless to say, it didn't work and today when booting up I get this:

fsck from util-linux-ng 2.16
/dev/sda5: clean, 264396/7618560 files, 9269181/30449191 blocks
[ 15.72092] uvcvideo: Failed to query (129) UVC probe control : -32 (exp.26)
{15.721199] uvcvideo: Failed to intialise the device (-5)
*Setting preliminary keymap
*Starting AppArmor profiles
*Startng init crypto disks
*cryptswap 1 (starting)
*cryptswap 1 (starting)
*Starting NVidia TV-Out server nvtvd
...done
*Starting Samba daemons
Speech-dispatcher configured for user sessions
*Starting the Winbind daemon winbind
*Starting Common Unix Printing system: cupsd
*PulseAudio configured for pre-user sessions
*Enabling additional executable binary formats binfmt-support
*Checking battery state....
..done
*Reloading Common Unix Printing system: cupsd


(The Speech-dispatcher and PulseAudio asterixs are in red)

I get the flashing cursor and nothing else happens.

I have gone in through the recovery console and in root shell have repaired broken packages (most seem to fail though).
I then went to the root shell and tried:
sudo apt-get remove xserver-xorg

I then reinstalled it, although it was unable to fetch some archives. 


Then when I tried to execute:
sudo dpkg-reconfigure xserver-xorg  

I got the message that xserver-xorg is broken or not fully installed.

When I reboot, same issue.

i can't ping servers.

How can this be fixed in recovery, when you can't seem to access the  repositories? 

I am very new to Ubuntu, so please do not assume I have any idea what I am doing here!

Any ideas on how to roll back these changes ?

Cheers

Max

Sony Vaio laptop VGN CR 353
Running Karmic
ATI Mobility Radeon&#8482; X2300

---

