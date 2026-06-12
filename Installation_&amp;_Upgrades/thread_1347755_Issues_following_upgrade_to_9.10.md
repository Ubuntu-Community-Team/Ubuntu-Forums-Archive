---
title: "Issues following upgrade to 9.10"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by Dom83 on 2009-12-06
[FONT=Verdana]Hi everyone,

I recently upgraded to Ubuntu 9.10 from 9.04 and have encountered three major problems since the upgrade:

1. I can no longer download software using the synaptic package manager and cannot update software sources. I get error message:

[/FONT][INDENT][FONT=Verdana]W: Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/karmic/Release.gpg)  Cannot initiate the connection to gb.archive.ubuntu.com:80 (2a01:450:10:1::10). - connect (101: Network is unreachable) [IP: 2a01:450:10:1::10 80]). [/FONT]
[/INDENT][FONT=Verdana]
I think that this might be something to do with ipv6 (no idea what that is!) because when I first upgraded I had no internet access but was able to ping IP addresses and website names. I found a post that told me how to disable ipv6 in Firefox but I couldn't complete the instructions to disable it globally by editing the grub because I have no file /etc/default/grub[/FONT][FONT=Verdana]. Any help with this would be greatly appreciated.

2. When I leave the computer alone for a while and the screen saver appears, on trying to use the computer again I either get very poor performance and an error message saying that there is no memory left (there should be plenty!) or I simply get a blank screen and am forced to cut the power to shut down.

3. Perhaps once every 5-10 times I log on I get an error message saying something like "temperature above threshold - CPU clock throttled". I often have to run fsck which is really annoying.

None of these problems appeared under 9.04 and I'm happy to revert back if that is the only solution but I don't want to lose my files.[/FONT]
[FONT=Verdana]
Thanks in advance!
Dom[/FONT]

---

