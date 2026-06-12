---
title: "On boot, &quot;broken pipe - could not write bits&quot;, but booted okay"
date: 2013-03-05
forum: Installation &amp; Upgrades
---

### Post by chavodel8 on 2013-03-05
I've read around and seen people with a similar error, but nothing quite the same. Many people seem unable to boot with this error, but I booted just fine. [This post]("http://askubuntu.com/questions/105857/ubuntu-11-10-not-booting-could-not-write-bytes-broken-pipes") seemed as close to my situation as I've found, but I do not seem to have the same issue as I don't have gdm installed, only lightdm.

When I boot (12.04.2 LTS), I see a "Broken Pipe - Could not write bits" error, followed by some other text that goes very quickly, then some text in red that said something about a battery state. Then I get my login prompt and log in just fine. I'm not sure what other information I can provide about the issue itself.

While it's not impeding my work, I'd like to resolve this if possible. It does give me a little angst as I'm concerned I may have a hard drive problem.

Some system information: I have two hard drives that had a raid set up with Windows. Due to lack of experience and concern of difficulty from my reading and searching, I decided to undo the raid configuration and switch back to ahci. I installed an instance of Ubuntu 12.04.2 on each, so two separate installs. I use sda1 primarily, but plan to occasionally mount sdb1 to create manual backups. (Perhaps not the most efficient way, but that's not the issue at hand.) I have nVida graphics cards with the nVidia Current-updates driver installed.

If I can provide any further info, please let me know what and I'll happily do so.

Thank you in advance, and thanks to all who answer so many other people's questions that resolve many of my own!
 -El Chavo

---

### Post by chavodel8 on 2013-03-06
Well, I never did anything for it, but it seems to have gone away. Sometimes I still get some messages popping up over the splash on startup. I'm not sure why, but things seem to be running smoothly. My sympathies to future readers as this will likely not be of much help.

---

### Post by schragge on 2013-03-06
If you are still in the mood to investigate it further then look for any spurs of "broken pipe" in */var/log/syslog*
E.g., open a terminal (**Ctrl**+**Alt**+**t**), and enter
```

zgrep -i 'broken pipe' /var/log/syslog*

```

---

