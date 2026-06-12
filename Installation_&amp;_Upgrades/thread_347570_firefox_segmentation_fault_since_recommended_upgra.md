---
title: "firefox segmentation fault since recommended upgrade"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by dilettante on 2007-01-27
I 'upgraded' to firefox 1.5.dfsg+1.5.0.9-0ubuntu0.6.06.1 today, as recommended by Update Manager. Now firefox won't start. Typing 'firefox' in a terminal window returns 'Segmentation fault'. I'm running Ubuntu 6.06 LTS.

When I first rebooted after the updates, I got several file system errors. I ran 'fsck' and answered Yes to any offer to fix issues.

As you may have gathered, I'm new to this Linux thing. Since my Ubuntu PC is mostly only used for web browsing, I'm rather hamstrung without firefox. Is there a way to revert my system to how it was, or can anyone suggest a way round this problem?

Thanks in advance.

---

### Post by taurus on 2007-01-27
Either try the new version of firefox or swiftfox.

[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Swiftfox)

---

### Post by dilettante on 2007-01-28
Thanks for your help, taurus

. I used Synaptic Package Manager to revert firefox to a previous version (1.5.dfsg1.5.0.3-0ubuntu3) rather than to a later version not suggested by ubuntu. 

In the process, I had to remove packages ubuntu-desktop and firefox-gnome-support. The first sounds important, though the system seems happy without it. If I try to reinstall ubuntu-desktop (even trying to use 'Force Version' to install an earlier Dapper version (0.119) rather than dapper-updates v0.120), package manager tells me I need to update firefox as well, which I don't want to do.

So do I just live without ubuntu-desktop, or is there another way?

Thanks for any help.

---

