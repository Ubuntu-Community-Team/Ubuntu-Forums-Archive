---
title: "PC reboot during installing 11.x --&gt; Ubuntu startup problems"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by HarryE on 2012-01-05
All,
As a new Ubuntu user, I decided to allow Ubuntu to upgrade from 10.?? to 11.0
All went well, but during the installation of 1 hour, my pc went into "sleep" modus, and it is impossible to get it out of this modus in Ubuntu.
 
So I had to reboot my pc, but during the start-up of Ubuntu the process stops somewhere at the point "checking battery status [OK]". Then everything just stops. I tried all Linux Ubuntu versions and save modii, the only thing that is still working is good old Windows XP, thank God!
 
What can I do to get my Ubuntu starting up again?
I do not like to start all-over with installing Ubuntu: then I will loose all my docs and pics that I've saved in the Ubuntu partition... help!
 
Thanks,
Harry

---

### Post by Paddy Landau on 2012-01-06
Lessons for next time: Disable power saving mode before upgrading! Back up all your data before installing!

Unfortunately, recovering from a failed installation is problematic. It may be possible but I'm not sure how.

Here is what I have, and I hope it works for you:

[LIST=1]
[*]When you boot, you are given the option between Ubuntu and Windows. Probably your second option is the "recovery mode".
[*]Choose the "recovery mode"; then "drop to root shell prompt".
[*]Type the following commands in order. (You may need to add [FONT=Courier New][SIZE=2]sudo[/SIZE][/FONT] to the front of each command.)
```
apt-get --fix-broken install
dpkg --configure --pending
apt-get ist-upgrade
```
[*]If step 3 works, you should be able to reboot and run Update Manager again.
[/LIST]
If, however, that does not work, you can try a different approach...

If you burn a Live CD (or preferably USB), you can boot from it to access your Ubuntu home folder. *Caveat:* If you encrypted your home folder, the following will not work without some sweat and tears.

[LIST]
[*]When you boot from the Live CD, find your /home/[username] folder in Nautilus.
[*]Check that you can see all your files in that folder.
[*]Press Ctrl-H so that you can see the hidden files and folders (those beginning with a dot).
[*]Now you need to back up everything in that folder. Copy the entire home folder to a safe place -- your Windows data area would be a good idea if there is space.
[*]Boot into Windows and check that your files really are there.
[/LIST]
Now, you can reinstall Ubuntu from scratch. Once you have recreated your user and successfully signed in, first run all updates. Then, copy the entire folder back again from Windows -- this will restore all your settings! All you need do is reinstall any programs you want installed.

This is a relatively painless procedure. I would always recommend a fresh installation over an upgrade, because I've seen too many problems with upgrades.

---

