---
title: "My detailed experience in switching to Kubuntu Karmic from 9.04"
date: 2009-10-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jetpeach on 2009-10-26
In case others find this useful, I wrote a report on installing Karmic (the RC, although it should be virtually the same for the final release). I chose not to upgrade my 9.04 and just do a new install, since it's quick to setup programs on Ubuntu and rsync to another computer works to backup my home directory so easily... For reference, I'm running a Dell Inspiron 1420n. Here's my experience.

*Installation*
Using Kubuntu Karmic Desktop 64bit version CD. Install paused at 80% while "configuring apt" for 5 minutes - I thought for a minute it had halted, but just needed to wait longer... But I consider this a bug, since an installer progress bar shouldn't stop for so long when it had been moving more rapidly before hitting this point...

Then near the very end, a "downloading language packs" message began....it took ~25 minutes to download the packs (and probably will take more if the servers are being hammered later.) I'm not certain why it even needed more language packs (I chose no special language, just English.) I heard this didn't happen in the betas, hopefully it won't happen during installs of the final release... Additionally, after installing there were already a lot of package updates, hopefully the final release won't have so many package updates immediately after installing (some are expected with the fast pace of improvements on Ubuntu, but this early I had 105 updates, which seems excessive...)

*After installation - "necessary" (IMO) configuration changes*
The bottom panel by default in KDE 4 is tiny. I had to make it bigger.

Enable extra repositories... my sources.list is here
[http://helpthehappy.com/09/sources.list](http://helpthehappy.com/09/sources.list)
and the GPG key commands are right below each source. Obviously this is just my list, but Medibuntu is probably the most important to add...

Enable restricted-driver (nvidia 185) - I just used the restricted-driver icon on the system tray.

Install kubuntu-restricted-extras, firefox, chromium-browser (w/chromium-codecs-ffmpeg-nonfree).
Remove icedtea - the freer java that never works well for me and I find conflicts with Sun's java.

Configure firefox (xmarks, adblock) -> Xmarks was having trouble connection, adblock took forever to download. are these strange connection problems? internet is fast on other machines and web browsing is fine...unknown cause, eventually worked.

Install pulseaudio - do others "believe" in pulseaudio on KDE? I've found I like it a lot and it seems to fix various sound problems, but I'm not sure why it isn't installed by default.
Then configure pulseaudio in system settings->multimedia to make it default for all sounds.
But upon testing and it gives only popping noises... believe I needed to add myself to pulse and pulse-access groups (system settings->advances->user management->choose account and modify->priviledges and accounts tab->under groups add check by pulse and pulse-access), restart.
Tested sound again and got nothing, but checked sound volume on kmix (system tray) and PCM was set to 0 (Why?! i didn't do it). Raised volume and worked, all is well now. While in kmix, enable additional channels (just Master, PCM, headphone, need microphone).

Configure dolphin to default to detailed view with no preview (under general icon, use common view properties) and show filter bar (under startup icon). I just don't like the default dolphin view with previews and even though it is suppose to remember for each folder what you change it to, you have to change each folders view manually before it remembers, and it doesn't always work right on network shares.

Add desktop folder to "places" (right click Desktop and choose add to places in dolphin).

Add folder view of home directory to desktop.

*Remaining questions: *
What the world is the "indicator display" message thing on the bottom right now?  All it says is "no applications running" and no way to configure...

*bugs that still exist: *
Full screen in flash, change volume with keyboard stroke and drops out of full-screen...

These stupid popup preview windows on folders that are super annoying, still no way to disable...many bugs filed on this already, they're working on it...

Above moving my Amarok2.1 collection database over, the collections works (after syncing music) but Amarok lost my statistics on my collection. If this also happens to people updating rather than moving a collection like I did, this could be a BIG deal for some. I've seen reports that make it sound like it does happen to upgraders, so be sure to backup your collection database before upgrading if you have a lot of ratings for songs that you care to keep. I have my songs/collectionDB backed up on a different computer, but unsure how to move the statistics at this time...

*Bug fixes and nice improvements*
Sound level is better for me (sound used to be quiet at 50% volume, and loud at 65%, now I actually can use full range and get better sensitivity).

Boot time for me is 36seconds. I think this is probably 10s faster than jaunty was, although i didn't record it w/jaunty...

Too many other bug fixes to mention and some I've already forgotten about since they're fixed!


*OVERALL THOUGHTS*
Karmic has a whole bunch of improvements. KDE users are still feeling the last of the growing pains in the switch to KDE 4, but they're almost gone and this was generally a smoother and much more pleasant experience than 9.04 or prior releases. Flash on 64 bit works fine, Virtualbox works fine, all the apps I need work great on 64 bit now (at this point, I recommend the switch to 64 bit because there really isn't any reason not too, even if you don't have 4gb or more of memory, since we should move to the new standard and encourage developers to optimize the speed for 64 bit...which often has significant speed improvements.)

---

