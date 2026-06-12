---
title: "update"
date: 2022-01-22
forum: Installation &amp; Upgrades
---

### Post by lanakalsel2 on 2022-01-22
E:can not open /var/lib/apt/lists/id.archive.ubuntu.com_ubuntu_dists_focal-updates_InRelease - fopen (13: Ijin ditolak), E:The package lists or status file could not be parsed or opened.

---

### Post by lanakalsel2 on 2022-01-22
Failed to fetch [http://id.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease](http://id.archive.ubuntu.com/ubuntu/dists/focal-updates/InRelease)  Tak dapat menyambung ke id.archive.ubuntu.com:80 (202.79.184.254), koneksi kehabisan waktu

---

### Post by Bashing-om on 2022-01-22
lanakalsel2; Hello -

Looks to me that you have at least 2 issues here.

Let us address the greater concern here of the  InRelease failure.
as
[http://id.archive.ubuntu.com/ubuntu/dists/](http://id.archive.ubuntu.com/ubuntu/dists/)
also fails for me, we can conclude that this is perhaps a bad URL.

Please post back the returns of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

and we verify your sources lists.
Then we can look at the probability of corrupted  MergeLists in apt.

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


[INDENT]longest journey starts with
[INDENT][INDENT]just one step
[/INDENT][/INDENT][/INDENT]

---

### Post by lanakalsel2 on 2022-01-23
1
     2  # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     3  # newer versions of the distribution.
     4  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish main restricted multiverse
     5  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish universe restricted multiverse main #Added by software-properties
     6
     7  ## Major bug fix updates produced after the final release of the
     8  ## distribution.
     9
    10  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    11  ## team. Also, please note that software in universe WILL NOT receive any
    12  ## review or updates from the Ubuntu security team.
    13  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish universe
    14  deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) focal-updates universe
    15
    16  ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    17  ## team, and may not be under a free licence. Please satisfy yourself as to 
    18  ## your rights to use the software. Also, please note that software in 
    19  ## multiverse WILL NOT receive any review or updates from the Ubuntu
    20  ## security team.
    21  deb-src [http://id.archive.ubuntu.com/ubuntu/](http://id.archive.ubuntu.com/ubuntu/) focal-updates multiverse
    22
    23  ## N.B. software from this repository may not have been tested as
    24  ## extensively as that contained in the main release, although it includes
    25  ## newer versions of some applications which may provide useful features.
    26  ## Also, please note that software in backports WILL NOT receive any review
    27  ## or updates from the Ubuntu security team.
    28
    29  ## Uncomment the following two lines to add software from Canonical's
    30  ## 'partner' repository.
    31  ## This software is not part of Ubuntu, but is offered by Canonical and the
    32  ## respective vendors as a service to Ubuntu users.
    33
    34  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-security main restricted multiverse
    35  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-security universe restricted multiverse main #Added by software-properties
    36  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-security universe
    37  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security universe
    38  deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security multiverse
    39                                                                                                                                                                                                   
    40  # This system was installed using small removable media                                                                                                                                          
    41  # (e.g. netinst, live or single CD). The matching "deb cdrom"                                                                                                                                    
    42  # entries were disabled at the end of the installation process.                                                                                                                                  
    43  # For information about how to configure apt package sources,                                                                                                                                    
    44  # see the sources.list(5) manual.                                                                                                                                                                
    45  deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) impish-security universe multiverse main restricted                                                                                                       
    46  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-security multiverse restricted #Added by software-properties                                                                                          
    47  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-updates universe multiverse main restricted                                                                                                               
    48  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-updates universe multiverse main restricted #Added by software-properties                                                                             
    49  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-backports universe multiverse main restricted                                                                                                             
    50  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-backports universe multiverse main restricted #Added by software-properties                                                                           
    51  #Manokwari Shell                                                                                                                                                                                 
    52   
    53   
    54  #Ubuntu 16.04 packages
    55   
    56  deb [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-proposed universe restricted multiverse main
    57  deb-src [http://mirror.0x.sg/ubuntu/](http://mirror.0x.sg/ubuntu/) impish-proposed universe restricted multiverse main #Added by software-properties
==> /etc/apt/sources.list.d/bind-dev.list <==


==> /etc/apt/sources.list.d/bind-dev.list.save <==


==> /etc/apt/sources.list.d/dotovr-ubuntu-manokwari-hirsute.list <==


==> /etc/apt/sources.list.d/dotovr-ubuntu-manokwari-hirsute.list.distUpgrade <==
deb [http://ppa.launchpad.net/dotovr/manokwari/ubuntu/](http://ppa.launchpad.net/dotovr/manokwari/ubuntu/) hirsute main
deb-src [http://ppa.launchpad.net/dotovr/manokwari/ubuntu/](http://ppa.launchpad.net/dotovr/manokwari/ubuntu/) hirsute main


==> /etc/apt/sources.list.d/dotovr-ubuntu-manokwari-hirsute.list.save <==


==> /etc/apt/sources.list.d/dotovr-ubuntu-manokwari-impish.list <==


==> /etc/apt/sources.list.d/dotovr-ubuntu-manokwari-impish.list.save <==


==> /etc/apt/sources.list.d/elementary-os-ubuntu-daily-hirsute.list <==


==> /etc/apt/sources.list.d/elementary-os-ubuntu-daily-hirsute.list.distUpgrade <==
deb [http://ppa.launchpad.net/elementary-os/daily/ubuntu/](http://ppa.launchpad.net/elementary-os/daily/ubuntu/) hirsute main
deb-src [http://ppa.launchpad.net/elementary-os/daily/ubuntu/](http://ppa.launchpad.net/elementary-os/daily/ubuntu/) hirsute main


==> /etc/apt/sources.list.d/elementary-os-ubuntu-daily-hirsute.list.save <==


==> /etc/apt/sources.list.d/endpoint-verification.list <==


==> /etc/apt/sources.list.d/endpoint-verification.list.distUpgrade <==
deb [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) endpoint-verification main # dimatikan untuk melakukan peningkatan ke hirsute
deb [https://packages.cloud.google.com/apt](https://packages.cloud.google.com/apt) endpoint-verification main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/endpoint-verification.list.save <==


==> /etc/apt/sources.list.d/forkotov02-ubuntu-ppa-focal.list <==


==> /etc/apt/sources.list.d/forkotov02-ubuntu-ppa-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/forkotov02/ppa/ubuntu](http://ppa.launchpad.net/forkotov02/ppa/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/forkotov02/ppa/ubuntu](http://ppa.launchpad.net/forkotov02/ppa/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/forkotov02-ubuntu-ppa-focal.list.save <==


==> /etc/apt/sources.list.d/google-chrome.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/google-chrome.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/google-chrome.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://dl.google.com/linux/chrome/deb/](https://dl.google.com/linux/chrome/deb/) stable main


==> /etc/apt/sources.list.d/iaz-ubuntu-battery-status-impish.list <==


==> /etc/apt/sources.list.d/iaz-ubuntu-battery-status-impish.list.save <==


==> /etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-1_1-focal.list <==


==> /etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-1_1-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/inkscape.dev/stable-1.1/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable-1.1/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/inkscape.dev/stable-1.1/ubuntu](http://ppa.launchpad.net/inkscape.dev/stable-1.1/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-1_1-focal.list.save <==


==> /etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-impish.list <==


==> /etc/apt/sources.list.d/inkscape_dev-ubuntu-stable-impish.list.save <==
deb-src [http://ppa.launchpad.net/inkscape.dev/stable/ubuntu/](http://ppa.launchpad.net/inkscape.dev/stable/ubuntu/) impish main


==> /etc/apt/sources.list.d/jonathonf-ubuntu-ffmpeg-4-hirsute.list <==


==> /etc/apt/sources.list.d/jonathonf-ubuntu-ffmpeg-4-hirsute.list.distUpgrade <==
deb [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/) hirsute main
deb-src [http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/](http://ppa.launchpad.net/jonathonf/ffmpeg-4/ubuntu/) hirsute main


==> /etc/apt/sources.list.d/jonathonf-ubuntu-ffmpeg-4-hirsute.list.save <==


==> /etc/apt/sources.list.d/kritalime-ubuntu-ppa-impish.list <==


==> /etc/apt/sources.list.d/kritalime-ubuntu-ppa-impish.list.save <==
deb-src [http://ppa.launchpad.net/kritalime/ppa/ubuntu/](http://ppa.launchpad.net/kritalime/ppa/ubuntu/) impish main


==> /etc/apt/sources.list.d/kubuntu-ppa-ubuntu-backports-focal.list <==


==> /etc/apt/sources.list.d/kubuntu-ppa-ubuntu-backports-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu](http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/kubuntu-ppa-ubuntu-backports-focal.list.save <==


==> /etc/apt/sources.list.d/linuxmint-daily-build-team-ubuntu-daily-builds-impish.list <==


==> /etc/apt/sources.list.d/linuxmint-daily-build-team-ubuntu-daily-builds-impish.list.save <==


==> /etc/apt/sources.list.d/me-davidsansome-ubuntu-clementine-focal.list <==


==> /etc/apt/sources.list.d/me-davidsansome-ubuntu-clementine-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu](http://ppa.launchpad.net/me-davidsansome/clementine/ubuntu) focal main


==> /etc/apt/sources.list.d/me-davidsansome-ubuntu-clementine-focal.list.save <==


==> /etc/apt/sources.list.d/microsoft-edge-beta.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main


==> /etc/apt/sources.list.d/microsoft-edge-beta.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main # dimatikan untuk melakukan peningkatan ke impish


==> /etc/apt/sources.list.d/microsoft-edge-dev.list.distUpgrade <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main


==> /etc/apt/sources.list.d/microsoft-edge-dev.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
# deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main # dimatikan untuk melakukan peningkatan ke impish


==> /etc/apt/sources.list.d/microsoft-edge.list <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main


==> /etc/apt/sources.list.d/microsoft-edge.list.save <==
### THIS FILE IS AUTOMATICALLY CONFIGURED ###
# You may comment out this entry, but any other modifications may be lost.
deb [arch=amd64] [https://packages.microsoft.com/repos/edge/](https://packages.microsoft.com/repos/edge/) stable main


==> /etc/apt/sources.list.d/mozillateam-ubuntu-firefox-next-impish.list <==


==> /etc/apt/sources.list.d/mozillateam-ubuntu-firefox-next-impish.list.save <==
deb-src [http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/](http://ppa.launchpad.net/mozillateam/firefox-next/ubuntu/) impish main


==> /etc/apt/sources.list.d/noobslab-ubuntu-icons-impish.list <==


==> /etc/apt/sources.list.d/noobslab-ubuntu-icons-impish.list.save <==


==> /etc/apt/sources.list.d/papirus-ubuntu-papirus-focal.list <==


==> /etc/apt/sources.list.d/papirus-ubuntu-papirus-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/papirus/papirus/ubuntu](http://ppa.launchpad.net/papirus/papirus/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/papirus-ubuntu-papirus-focal.list.save <==


==> /etc/apt/sources.list.d/ricotz-ubuntu-docky-focal.list <==


==> /etc/apt/sources.list.d/ricotz-ubuntu-docky-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/ricotz/docky/ubuntu](http://ppa.launchpad.net/ricotz/docky/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/ricotz/docky/ubuntu](http://ppa.launchpad.net/ricotz/docky/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/ricotz-ubuntu-docky-focal.list.save <==


==> /etc/apt/sources.list.d/saiarcot895-ubuntu-chromium-beta-focal.list <==


==> /etc/apt/sources.list.d/saiarcot895-ubuntu-chromium-beta-focal.list.distUpgrade <==
deb [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute
deb-src [http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu](http://ppa.launchpad.net/saiarcot895/chromium-beta/ubuntu) hirsute main # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/saiarcot895-ubuntu-chromium-beta-focal.list.save <==


==> /etc/apt/sources.list.d/spotify.list <==


==> /etc/apt/sources.list.d/spotify.list.distUpgrade <==
deb [http://repository.spotify.com](http://repository.spotify.com) stable non-free # dimatikan untuk melakukan peningkatan ke hirsute


==> /etc/apt/sources.list.d/spotify.list.save <==


==> /etc/apt/sources.list.d/strukturag-ubuntu-libde265-impish.list <==


==> /etc/apt/sources.list.d/strukturag-ubuntu-libde265-impish.list.save <==


==> /etc/apt/sources.list.d/team-xbmc-svn-ubuntu-ppa-impish.list <==


==> /etc/apt/sources.list.d/team-xbmc-svn-ubuntu-ppa-impish.list.save <==


==> /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-impish.list <==


==> /etc/apt/sources.list.d/teejee2008-ubuntu-ppa-impish.list.save <==


==> /etc/apt/sources.list.d/tomtomtom-ubuntu-conky-manager-impish.list <==


==> /etc/apt/sources.list.d/tomtomtom-ubuntu-conky-manager-impish.list.save <==


==> /etc/apt/sources.list.d/trinity-builddeps.list <==


==> /etc/apt/sources.list.d/trinity-builddeps.list.save <==


==> /etc/apt/sources.list.d/trinity.list <==


==> /etc/apt/sources.list.d/trinity.list.save <==


==> /etc/apt/sources.list.d/ubuntudde-dev-ubuntu-stable-impish.list <==


==> /etc/apt/sources.list.d/ubuntudde-dev-ubuntu-stable-impish.list.save <==
deb-src [http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu/](http://ppa.launchpad.net/ubuntudde-dev/stable/ubuntu/) impish main

---

### Post by lanakalsel2 on 2022-01-23
thanks for fast respon

---

### Post by ajgreeny on 2022-01-23
@ lanakalsel2

Unfortunately your post at #4 is far too difficult to read and interpret as you did not reply using code tags for any terminal output as requested in post #3 by Bashing-om.

Can you please post again but this time copy and paste the terminal commands and output by highlighting the text with your mouse, right click to copy, and the paste into the reply box in this thread in code tags as explained at [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

---

### Post by Bashing-om on 2022-01-23
lanakalsel2; We begin the journey :D

1) id.archive.ubuntu.com/ubuntu/ :
resolves to ossmirror.mycloud.services and times out.

The hosting country appears to be Singapore and that raises the concern that this outage is in relations to international politics ?
```

ping -c3 id.archive.ubuntu.com
PING ossmirror.mycloud.services (202.79.184.254) 56(84) bytes of data.

--- ossmirror.mycloud.services ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2050ms

```
for the time until the issue is resolved at that distant end I do suggest that the source be disabled.

2) non-impish software repositories:
Please remove all other instances or update to reflect impish rather than either focal or hirsute.
Please see: [https://ubuntuforums.org/showthread.php?t=2338595](https://ubuntuforums.org/showthread.php?t=2338595) for the reasoning that such is a bad bad idea.

3) Once your /sources.list(s) files are in a consistent state we can then address the corrupted mergelist.

[INDENT]we make haste
[INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2022-01-24
lanakalsel2;; Hey Hey :D

id.archive.ubuntu.com is back in service (re-directed ?):
```

ping -c3 id.archive.ubuntu.com

PING archive.ubuntu.com ([color=green]91.189.88.152[/color]) 56(84) bytes of data.
3 packets transmitted, 3 received, 0% packet loss, time 2003ms

```

[INDENT]All in good time
[/INDENT]

---

