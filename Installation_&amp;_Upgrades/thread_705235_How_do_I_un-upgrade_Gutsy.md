---
title: "How do I un-upgrade Gutsy?"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by JontomXire on 2008-02-23
Hi, everyone.

I recently upgraded my Feisty Fawn installation to Gutsy Gibbon as a first step in trying to solve the Xorg using 100% CPU issue. I had seen a lot of people saying that they didn't see the problem with Gutsy or had found a fix. I have a temporary saver in place: a cron job that runs every minute, tests Xorg CPU consumption, and kills the process if it is being too greedy.

Well first, I didn't have the graphical upgrade tool, so after a lot of searching and ignoring all the instructions that said to use the graphical upgrade tool, I figured out "upt-get dist-upgrade".

Halfway through the upgrade Xorg started hogging CPU, my saver script kicked in, and the whole X server, the terminal program, and shell and everything else went byebye.

I logged back in when the X server restarted itself, opened a terminal, and with the help of man pages managed to fix the installation, and finish the upgrade. I then ran out of time at the actual machine as I had to go pick up my girlfriend, but not before realising that the Xorg CPU hog still existed with Gutsy too.

All was well for a couple of days until the server crashed. Completely. As I only have remote access during the week, I was unable to do anything with the machine until the weekend at which time I checked the system logs and found ... nothing. They just stopped logging anything at around the same time. While I was there I used Envy to try using the NVidia drivers to fix the Xorg problem, and found, just before I had to leave, that actually that just made the desktop completely unusable.

By Monday the whole machine had crashed again.

Well this weekend I managed to use the Feisty install CD to access the xorg.conf and go back to using the "nv" drivers. My conclusion is that Gutsy is a pile of sh1te. Feisty may have the desktop hang/Xorg CPU hog problem, but as a basic web/ssh/ftp/whatever server it works wonderfully.

I'd rather not re-install from scratch. I want to simply uninstall Gutsy and go back to Feisty. Can anyone tell me how?

If anyone can also give me some clues as to how to fix the Xorg problem as well that would be wonderful. I've been reading the forums endlessly and the conclusion seems to be to use Nvidia drivers and then adjust this or that config. However, anything except the vanilla drivers that get installed initially just makes the desktop really unusable.

---

### Post by Partyboi2 on 2008-02-23
You could try [this]("https://help.ubuntu.com/community/DowngradeHowto"), but can't guarantee it will work

---

