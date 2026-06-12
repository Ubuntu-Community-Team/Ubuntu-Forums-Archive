---
title: "Firefox 3 and Firefox 2 installation"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by EliBaskin on 2008-04-09
Well, I was trying this whole Firefox 3 thingie, didn't like it that much yet (not enough plugins that support FF3, yet), so I used synaptic to remove Firefox3 and reinstall Firefox2.

And here the weird thing begins.

When I click on the FF icon on the navigation bar (which runs /home/myhomedir/firefox/firefox), FF3 launches! "Weird", I thought to myself. So I started FF from the menu (Applications->Internet->Firefox Web Browser) - and what do you know? Firefox 2 started!

Now the really weird thing happens. When Firefox 2 is running, and I click on the aforementioned icon on the navigation bar, it opens FF2, and not FF3! However, when I close FF2, and click on that very same icon, it starts FF3!

Confused? So am I.

Why do you thing this happens and how can I fix it?

P.S.
I realized that in the beginning I didn't install Firefox3 using synaptic, but via command line, using instructions on one of the blogs... Dumb, I know.

---

### Post by PmDematagoda on 2008-04-09
Could you please provide some details pertaining to exactly how you installed it?

---

### Post by EliBaskin on 2008-04-09
I am pretty sure I used the instructions as described in the following link:

[http://tombuntu.com/index.php/2008/04/03/install-firefox-3-beta-5-in-ubuntu-with-one-command/](http://tombuntu.com/index.php/2008/04/03/install-firefox-3-beta-5-in-ubuntu-with-one-command/)

Here is the quote:
======================================================
Backup your profile
Before you run Firefox, you may want to backup your profile from Firefox 2. I haven’t had any problems sharing the profile so far, but don’t let Firefox 3 update update your extensions when it starts to avoid incompatibilities. This command will backup the Firefox profiles folder to firefox_profile_backup in your home folder:
cp -r ~/.mozilla/firefox/ ~/firefox_profile_backup

If you need to restore from the backup, do so by replacing the hidden .mozilla/firefox folder with your backup.

Install Firefox 3 Beta 5
Let’s install Firefox now. This one command downloads the Firefox archive, and extracts it to a folder called firefox in your home directory. Copy and paste it (one line) into your terminal to install.
wget -O - [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/linux-i686/en-US/firefox-3.0b5.tar.bz2](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b5/linux-i686/en-US/firefox-3.0b5.tar.bz2) | tar xj -C ~

Run Firefox 3 Beta 5
Before running Firefox 3, close Firefox 2. Double-click the firefox file inside the firefox folder in your home directory, or run this command:
~/firefox/firefox
========================================================

---

### Post by billynomates on 2008-04-09
This happens to me too. It's something to do with shared configuration files.
What is the command that is behind the menu option? (Right click on the menu on the panel, edit menus, find FF2, right click, properties, command)

---

### Post by EliBaskin on 2008-04-09
The command is firefox %u

---

### Post by billynomates on 2008-04-09
What exactly did you uninstall in synaptic? Dide you uninstall firefox-3.0-gnome-support as well?

---

### Post by EliBaskin on 2008-04-09
Yep. I've uninstalled everything that had 'firefox' and '3' in it :)

---

### Post by billynomates on 2008-04-09
Have you tried uninstalling everything for both (FF2 and 3) and then reinstalling FF2?
If you have, I'm all out of ideas! :confused:

---

### Post by PmDematagoda on 2008-04-09
From the instructions it looks to me that you did not install Firefox as in compiling, but you just downloaded the archive and is just running a ready-made executable.

So if you followed the instructions exactly as they were given then you should be able to uninstall Firefox with:-
```
rm -R ~/firefox
```
and then change the launcher on the top menu to launch Firefox 2 instead of Firefox 3.

---

### Post by ynef on 2008-04-09
Firefox uses a start up script that checks if there's already an instance running (in order to open links clicked in other programs in tabs, among other things). So, you'll have to muck around quite a bit to get FF2 and FF3 running at the same time (and I would advice against it, since they share a profile unless you've done some creative stuff with that).

This will also happen in you run Firefox locally and then try to open it via X forwarding from somewhere else -- all that happens is that a new local window shows. Very annoying.

---

### Post by EliBaskin on 2008-04-10
> **PmDematagoda said:**
> From the instructions it looks to me that you did not install Firefox as in compiling, but you just downloaded the archive and is just running a ready-made executable.

So if you followed the instructions exactly as they were given then you should be able to uninstall Firefox with:-
```
rm -R ~/firefox
```
and then change the launcher on the top menu to launch Firefox 2 instead of Firefox 3.


Thank you, it had worked.

---

