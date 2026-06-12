---
title: "Moving to new machine /home problems"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by Mylorharbour on 2009-11-29
We have a netbook running Hardy but are trying to move to another running a newly installed Karmic Netbook Reloaded OS with Thunderbird installed. We used Simple Backup to backup /home on the old machine and Simple Backup Restore to restore it to /home on the new machine. Both installations have the same solitary user account name. 

The problem is that although the ~/home/username/.mozilla-thunderbird folder is overwritten by the backup, complete with the old emails presumably, Thunderbird doesn't show them at startup. It just wants us to set up a new email account. Firefox doesn't read the old bookmarks either (from the .mozilla folder). What else do I need to do?

---

### Post by oldfred on 2009-11-30
You need to open thunderbird first to create an initial profile.ini and profile default. Then edit these to your new files.
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

You may be able to use the newer profile manager.

[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)


[LIST]
[*] *(Firefox)* ./firefox -profilemanager
[*] *(Mozilla Suite)* ./mozilla -profilemanager
[*] *(SeaMonkey)* ./seamonkey -profilemanager
[*] *(Thunderbird)* ./thunderbird -profilemanager
[/LIST]

---

### Post by Mylorharbour on 2009-12-01
Thanks oldfred, I got there in the end.

For anyone else having this problem restore /home to your new /home area/partition, open TB, set an email address, close TB. This will create a profile folder in the /.mozilla-thunderbird folder (xxxxxx.default). This is referenced in the path= line in the profile.ini file. Edit this path= line to point to the restored profile folder, save, close. Open TB and your emails should miraculously appear.

The procedure is also very similar for Firefox bookmarks & cookies. These profiles are in the /.mozilla folder.

---

### Post by SaintDanBert on 2010-01-07
> **Mylorharbour said:**
> Thanks oldfred, I got there in the end.

For anyone else having this problem restore /home to your new /home area/partition, open TB, set an email address, close TB. This will create a profile folder in the /.mozilla-thunderbird folder (xxxxxx.default). This is referenced in the path= line in the profile.ini file. Edit this path= line to point to the restored profile folder, save, close. Open TB and your emails should miraculously appear.

The procedure is also very similar for Firefox bookmarks & cookies. These profiles are in the /.mozilla folder.

Begin_Cranky

WHY IS ALL OF THIS SO MUCH MAGIC -- BLACK, WHITE or OTHER?

We all move between machines or move to larger hard drives or similar?!

We all religiously backup our $HOME tree and need to restore things??!!

Why doesn't software (1) notice that the restored profile is different some how, and (2) give the end-user the opportunity to integrate the old with the new?

While I'm at it:  Why don't we have /home/.mozilla/ and then the separate applications ../firefox  ../thunderbird  ...?

End_Cranky

~~~ 0;-Dan

---

