---
title: "Is Metacity Gone in 12.10? Compiz Still Works but Gtk-Window-Decorator Crashes."
date: 2012-10-26
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2012-10-26
I've had all sorts of wackiness besiege me since upgrading to 12.10 last night, like the system boot halting because it couldn't mount an NTFS volume ([https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726?comments=all](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1059726?comments=all)), no file manager at all when I did manage to log in ([http://ubuntuforums.org/showthread.php?p=12320238#post12320238](http://ubuntuforums.org/showthread.php?p=12320238#post12320238)), and now all sorts of weirdness with my window manager(s).

When the titlebars suddenly disappeared, I did the good old **metacity --replace** and it made things worse. Now, I couldn't see any complaint in the terminal about Metacity not being installed, and indeed something did happen when I ran that, being that I could use any windows open, but none would come to the foreground, and any totally out of view (either being behind larger windows, or minimised) could not be accessed at all, since the taskbar buttons (in Gnome 3 Classic/Fallback) did nothing.

I managed to get things back as they were by running **compiz --replace**, which I had to do when logging into 12.10 for the first time (not so much as the effects were missing, but I couldn't use multiple workspaces). However, till now I've quite often replaced Compiz with Metacity, as while I got back Compiz in Classic Desktop with the 12.04 upgrade, "fullscreen" in any app had the top and bottom panels showing, whereas with Metacity I get proper FULLscreen.

Also, I noticed via crash reports that have popped up since the 12.10 upgrade that **gtk-window-decorator** (which I'm unfamiliar with) is apparently trying to run the show, but fails, and **gtk-window-decorator --replace** just causes another crash report.

So any ideas of the state of things (windows management and decoration wise) in 12.10? Has Metacity been replaced or disabled, or conflicting with something? I see Metacity is available for Quantal, so should I install it? And will there be any consequences if so? Any help on this would be welcome.

(PS: I just tried Image Viewer (eog) with Compiz running and a welcome turn of events is that it remains totally fullscreen, as does Firefox, meaning I don't need to revert to Metacity each time I want to use an app in fullscreen. However, I'd still like to know if I can get Metacity running, as there are those times Compiz fails, and refreshing it doesn't do the trick, but replacing it Metacity does).

---

### Post by mc4man on 2012-10-26
metacity is a dep of gdm & gnome-session-fallback (gnome-session also deps on because it deps on  gdm.

So if using Classic or Classic(no effects), then metacity should have been installed.

(libmetacity-private0a is a dep of compiz/unity so would be default installed

Classic (compiz) is still liable to have inconsistent behavior though can work ok, at least for a while.

If you upgraded with some of the gnome ppa's then small issues would be likely to occur from the upgrade though nothing you can't resolve
(based on other post it seems you have the gnome3 ppa, no other way to get nautilus-3.6.1 in 12.10 which is by default using 3.4.2 (1:3.5.90.really.3.4.2-0ubuntu4

---

