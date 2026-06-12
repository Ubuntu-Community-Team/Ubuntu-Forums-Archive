---
title: "New Kernel 3.13.0-44 on Ubuntu 14.04 breaks sound and wifi"
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by danfan46 on 2015-01-14
After installing new linux kernel 3.13.0-44 I have no sound and no wifi.
Rebooting on 3.13.0-43 everything is OK again.

---

### Post by danfan46 on 2015-01-14
Truly, 3.13.0-4 was installed the 13th of Jan. On the 11th I was trying to remedy a problem with timidity and pulseuadio (sound clipping and 100% CPU usage). Following the advice on help.ubuntu.com/community/SoundTroubleshootingProcedure  i executed this command:
[I]sudo apt-get update;sudo apt-get dist-upgrade; sudo apt-get install pavucontrol linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; sudo apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop  linux-image-`uname -r` libasound2; killall pulseaudio; rm -r ~/.pulse*; ubuntu-support-status; sudo usermod -aG `cat /etc/group | grep -e '^pulse:' -e '^audio:' -e '^pulse-access:' -e '^pulse-rt:' -e '^video:' | awk -F: '{print $1}' | tr '\n' ',' | sed 's:,$::g'` `whoami`
[/I]**This is logged in apt/history.log as:**[I]
Commandline: apt-get -y --reinstall install linux-sound-base alsa-base alsa-utils lightdm ubuntu-desktop linux-image-3.13.0-43-generic libasound2
Reinstall: linux-image-3.13.0-43-generic:amd64 (3.13.0-43.72), ubuntu-desktop:amd64 (1.325), alsa-base:amd64 (1.0.25+dfsg-0ubuntu4), alsa-utils:amd64 (1.0.27.2-1ubuntu2), linux-sound-base:amd64 (1.0.25+dfsg-0ubuntu4), libasound2:amd64 (1.0.27.2-3ubuntu7), libasound2:i386 (1.0.27.2-3ubuntu7), lightdm:amd64 (1.10.3-0ubuntu2)
[/I]
This is probably the reason why I have no sound  after upgrade. But I don't know why and how to fix it.  
/dg

---

