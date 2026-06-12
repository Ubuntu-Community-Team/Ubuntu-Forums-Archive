---
title: "How my update went"
date: 2006-06-09
forum: Installation &amp; Upgrades
---

### Post by SteveF on 2006-06-09
I've seen a lot of questions regarding the upgrade to Dapper (some of them are my own).  I decided to post this note with my mostly positive opinionjust saw people looking in can see that on a whole, upgrades can work out pretty well and also to let the developers that I appreciate their effort.

I had two partitions on my machine running Breezy, one running Kubuntu and one running Ubuntu.  Since I mostly run Ubuntu, I decided to update Kubuntu first and use it for a little while before updating Ubuntu.  I modified my sources to point to Dapper, ran the appropriate apt-get commands and responded to a couple of questions regarding overwriting some configuration files that changed.

Issues I ran into:
1) The configuration change questions.  Most new users will not know what to answer.  I wonder if the wording could be modified to give the user a better hint as to which to answer.  I'm not sure what that would be and I ended taking the new ones (except for Vim which I know I modified and wanted kept).

2) Amarok was uninstalled.  I'm not sure why (uses Xine instead of Gstreamer now??).  It was an easy reinstall and was not a big issue to me.

3) OpenOffice was uninstalled.  Again no idea why.  It took two tries to get this installed.  The first time, I selected the main OpenOffice package, but only some language packages got installed, none of the apps.  The second time, I ended up having to select all of the main apps (sheet, write, etc) in order to get it installed.  This was not difficult, just confusing.

4) My machine froze during restart.  This seemed like a major issue at the time until I realized the nvidia drivers were not working after the upgrade.  I don't think they are offically supported (is that true) so I understand that I can't expect Kubuntu to fix the issue.  I wonder if a word of warning should be in the dts-upgrade though.  Something like "if you installed proprietary video drivers, you may want to uninstal them prior to running the upgrade".

5) I thought I lost sound.  The default looks to be to set the WAV setting to zero.  This may have also occurred because of the way I answered the config questions to use the new ones.  Like was mentioned in a response to one of my posts, maybe zero is not the best default to use.

6) Adept Updater no longer exists in the menus.  Kubuntu now has the auto-update icon so maybe the developers felt it wasn't needed anymnore.  Not sure, but confusing.

All in all, nothing too bad.  I had an upgraded OS and most of my apps were intact and working.

Next step was to upgrade Ubuntu.  Ubuntu has the update manager which i think made updating a lot easier.  I didn't have to modify my repositories and when the questions came up about config files, it showed the diff in the popup (I think apt-get would show the diff, but I don't remember it).

Issues I ran into:
1) K3b was uninstalled (not sure why).  Easy fix with Synaptic.

2) I was warned that if I had universe then gstreamer 8 would not be uninstalled and that is exactly what it did, not unintall it.  Not really an issue since I chise to let it happen, just not sure why it had to happen.  I ended up manually uninstalling it through Synaptic.

3) Because I uninstalled gstreamer 8, GnomeBaker got uninstalled.  I use K3B mostly so not a biggie for me.  Just curios as to why GnomeBaker needed gstreamer 8 instead of 10.  Is that a package decision or a developer decision?

4) For ripping mp3 files I use SoundJuicer.  In Breezy I installed gstreamer-lame and/or gstreamer-mad (I forget).  Now it wants gstreamer-ffmpeg.  I know mp3s are not fully supported because of restricted format issues so slightly annoying.

5) Numlockx wasn't working.  I had to reinstall.  No idea why.

6) The one (what I would call) major issue.  Linux 2.6.15 was not added to Grub.  I have no idea why.  From an update standpoint, easy to fix, but now requires two restarts instead of one (one to see it is missing from Grub and one to actually boot into the new version of Linux).

Again, nothing too bad (except for the Grub issue) from an upgrade standpoint.  Again all apps working no major reinstalls.    Most of the time, doing OS upgrades I would now still be reinstalling all of my software so I am definitely not complaining about the minor issues I have.  To have two upgraded systems for a couple of hours of work (most of that downloading) is not bad at all.

I know others have had more major issues.  I just wanted the developers to know that not all did and to inform them of some minor nuisances to look at.

Steve

ps.  I liked the brown (maybe one fo the few??), not sure if I'm as hot on the orange.  But what do I know.

---

### Post by keithjr on 2006-06-09
[QUOTE=SteveF]

6) The one (what I would call) major issue.  Linux 2.6.15 was not added to Grub.  I have no idea why.  From an update standpoint, easy to fix, but now requires two restarts instead of one (one to see it is missing from Grub and one to actually boot into the new version of Linux).
[/QUOTE]

That is VERY odd...Although  I've had similar problems where the kernel version would get added to grub after a new kernel upgrade but would need to get manually set as the default, which is only a minor annoyance.  However, I did the same Breezy-Dapper upgrade just the other day and the grub entry was made... wonder what happened to yours...

---

### Post by SteveF on 2006-06-09
When I did the Kubuntu one, it updated the local grub menu (I have grub coming from  Ubuntu so Kubuntu's version just sits on the hard drive unused), so I was surprised when grub was not updated for Ubuntu.

Steve

---

