---
title: "Server 22.0.43 Jammy installation failing"
date: 2024-10-14
forum: Installation &amp; Upgrades
---

### Post by sgt-mike on 2024-10-14
I get up to the configure Ubuntu achieve mirror 
[http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
and installation fails
```
 
Reading package lists
E: Release file for http://archive.unbuntu.com/ubuntu/dists/jammy-updates/InRelease is not valid yet (invalid for another 327d 19h 52min 31s) . Updates for this repository will not be applied.
E: Release file for http://archive.unbuntu.com/ubuntu/dists/jammy-backports/InRelease is not valid yet (invalid for another 327d 19h 52min 31s) . Updates for this repository will not be applied.

```

Any one know a working mirror 
or should I just update my installing media to a more recent version of server? As I had intentions of updating to once I had the updates applied after installing a OS

---

### Post by 1fallen on 2024-10-14
This sounds to me like a Clock/Time issue, unless you have been seeing that for multiple days.
Check if ti is correct:
```
[FONT=monospace][COLOR=#000000]timedatectl[/COLOR]

```



[/FONT]

---

### Post by oldfred on 2024-10-14
I thought archive was only for obsolete versions.

Current mirrors:
[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

There used to be a really good one in Chicago area, but it shutdown.
And in synaptic you used to be able to select repostory.
System, Administration, Synaptic, settings, Repositories, download from combo box, other, Select best server.
But best server is just based on ping, not necessarily speed.
Just tried again, and it would not load. Not sure if system slow or what issue is.

---

### Post by sgt-mike on 2024-10-14
Thanks oldfred that will help

I did the download of a newer version (noble) wrote over my install USB.... This time let me install even though it kept erroring on the Mirrors during installation.... 
ran a apt update again error ....
1Fallen is all over it ........  Dummy me decided to stick that used MB/cpu in a case  it is that I told Fallen about in a PM . 
I updated the bios version to the most recent from Asus. 
set the time date in the bios. booted from the USB installed ...
ran command as Fallen stated timedatectl  noticed RTC off by years 2009 to be exact ......   Stupid CR 2032 battery ..... and I usually put a new battery is when I do this..... Grrrrrr haste  
I should have caught that .....
Thanks everyone I'll shutdown  the new server and replace the battery and go from there

---

### Post by 1fallen on 2024-10-14
lol It happens to the best of us.

---

### Post by sgt-mike on 2024-10-14
I know I just hope everyone is laughing as hard as I am at myself... Talk about a Derrp moment
Yeah the tell tell was had just updated the time and date in the Bios and then when I seen the RTC time I knew what it was. dead battery.

--------------------------------------------------------------------------------------------------------------------
This part was added via edit after about 24 hours of running down the actual underlying issue once a new battery was in place:

A little bit after the new battery install, the machine was still giving me sync issues with time, again causing the same sort of issues with repositories. not enough to really affect updates, but enough to bug me. I then wiped Ubuntu server off that machine went for a fresh install of Arch, which at first had the same issues. What I mean by issues is they would install and attempt a update yet one sometime two repositories failed randomly. 
Turns out the main culprit was the  [COLOR=#000000][FONT=Verdana] /etc/systemd/timesyncd.conf  file in both OS's. Both shipped commented out which I kind of understood why too many variables and actually requires input from the end user to work. When installing Arch I could edit the file and update the commented NTP areas with actual servers allowing the RTC to almost synch up the NTP clocks pre installation never  a issue arose .  With the pre install edits, Arch would install happily. Once complied and completed. The issues turned out to be that time never synched up causing a inability to access all the default repositories' when installing post installation tweaking = success. Now this part will be a unfair statement but is a observation of my hardware. Arch was not performing as well as my desired level on _THAT motherboard /CPU/GPU chipset combo_, I suspect that it had to do with the way Asus utilized the chipset. I'm in NOWAY attempting to slam Arch as it is  fine choice and I did like Arch. Just my combo wasn't working to the level I desired. Had I had more experience with Arch and not been impatient. I'm positive that I could have tuned everything to high degree of satisfaction. That is a fallacy of the end user (me) not the OS. 
So I went back to Ubuntu after a bit of editing and tweaking post installation. Finally time was synched up enough that issues went away. I did finally get the RTC/NTP etc to fully synchronize.  
[/FONT][/COLOR][COLOR=#000000][FONT=Verdana]
[/FONT][/COLOR]```

[COLOR=#000000]#  This file is part of systemd.[/COLOR]
#
#  systemd is free software; you can redistribute it and/or modify it
#  under the terms of the GNU Lesser General Public License as published by
#  the Free Software Foundation; either version 2.1 of the License, or
#  (at your option) any later version.
#
# Entries in this file show the compile time defaults.
# You can change settings by editing this file.
# Defaults can be restored by simply deleting this file.
#
# See timesyncd.conf(5) for details.

[Time]
#NTP=
#FallbackNTP=ntp.ubuntu.com
#RootDistanceMaxSec=5
#PollIntervalMinSec=32 
#PollIntervalMaxSec=2048
```[COLOR=#000000][FONT=Verdana]

The actual reason for adding this part isn't to slam a OS. That included part is just background information experience. It is to actually point out to other users regardless of Linux flavor that experience's similar issues. Where to investigate to resolve their issue.  In my case I simply uncomment NTP= (inserted the google time server) and uncomment the FallbackNTP line saved the file and restarted service, tweaked it to synching RTC and NTP time. Worked for both OS's. Would I install Arch server again?  absolutely.  On a different machine hardware. Is there other areas of that the server OS require some attention yes, but is another post.



[/FONT][/COLOR]

---

