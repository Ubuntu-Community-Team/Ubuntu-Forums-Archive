---
title: "VLC, KDE4, updates tonight and THAT line of screen tearing NVidia bug"
date: 2009-11-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-11-18
Anyone else found tonight that VLC suddenly will no longer go completely fullscreen on KDE4? Some update tonight has forced two problems:
[LIST]
[*]The panel is now forced on the screen, you can remove it by setting the windows can cover panel option via the panel settings, but of course, when I select fullscreen, I kind of expect fullscreen, panel or no panel...
[*]This has a sting in the tail for anyone with a NVidia card and a dual monitor setup. Whilst I work on one monitor, I use the other monitor to view and test DVB-T. Before, with the XVideo video output, the NVidia VSync and the dreaded line of screen tearing which would creep up the screen would be ignored and you would be able to view VLC on one monitor and work on the other without tearing on either screen. Since tonight's update, the monitor which shows VLC (and it doesn't matter which monitor it is or how you set it up, Murphy's Law dictates it will always be the monitor you use for video!) will now have the dreaded line of screen tearing.
[/LIST]
I started a bug on it: [https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/485030](https://bugs.launchpad.net/ubuntu/+source/vlc/+bug/485030) which also includes a snapshot of the bug in action from my DVB-T card.

---

