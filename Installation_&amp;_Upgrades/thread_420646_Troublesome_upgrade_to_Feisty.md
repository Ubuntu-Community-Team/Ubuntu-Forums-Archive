---
title: "Troublesome upgrade to Feisty"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Keith_Beef on 2007-04-23
Tried upgrading from 6.06 to 6.10 using the alternate install disc. This seemed to work.

So I tried to upgrade to Feisty Fawn, and at the end of about six hours had no X Window system.

"Fatal server error: could not open default font 'fixed'".

So I booted from a Knoppix live disc to get back on-line and seek a workround.

I found that "sudo dpkg-reconfigure xserver-xorg" would allow me to reconfigure X, but this told me that X was not properly installed at all.
So I tried "sudo apt-get install xserver-xorg" and was then able to do "startx".

Tried using the package manager to upgrade to Feisty Fawn, and at the end of about four hours I got an error message like

"shift 96: Can't shift that many"

Rebooted,
update manager suggested an upgrade, chose Yes.

This informed me that I would upgrade to 6.10, then popped up an alert box:

Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.


So I decided to simply update existing system; 689 packages to download!

Part way through, I get a popup message from Debconf, or something, with missing fonts (a message about a Pango library in in the "details" window of the update manager at this moment). And through clumsiness, I dismiss this box without knowing how...

And at the end of al this, I get a message
"Not all updates can be installed, run a distribution upgrade"...

And when I do that, a sudo box pops up for me to enter my password. Luckily, I know what it is, because the text is replaced by little boxes! Is this the damned pango text rendered again?

Even Synaptic does this now. I can't do much at all, because I can't read the dialog boxes!

Well, after leaving it overnight, and coming back to it today, I got a message from the update manager that there were still packages that needed to be updated.

I clicked on the button to go ahead, and now all the problems seem to have been cured. No more missing fonts, no more error messages.

Sound never stopped working, either.

Moral of the story: make sure you have a bootable live Linux, so you can go hunting for answers.

Beef.

---

### Post by zvacet on 2007-04-24
Maybe it was just bad download(corrupted files).You can repair it easy without doing full download.Choose download with torrent,and point download to the folder with existing iso.If you have some files corrupted only them will be changed and you will have proper iso.You don´t need live linux CD to boot.Gparted Live CD is enough.
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

