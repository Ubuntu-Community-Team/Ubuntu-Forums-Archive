---
title: "Reinstalling Ubuntu over old Install"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by willthebold on 2008-08-25
Hey all, is it possible to reinstall Hardy Heron over an install that's already there without wiping all your personal files. Basically, I did a LOT of tinkering with the OS when I first got it because things were new and exciting, but I want to get everything off that's not in the original install. Is there a good way to go about this? Thanks.

---

### Post by gatenby_jp on 2008-08-25
If you did the original install as a flat file system ... without partitions for /home then you would need to boot with a live cd and use gparted to create a partition big enough for you to move your data onto.
once you have created the partition you will need to mount it then copy your data across. Now on the re-install choose manual partitioning ... delete the partition which contains your old system ... careful not to delete the new one ... then create the partition all over again and set its mount point as    / and to format
next select the partition with your data and manually set the mount point as /backup ... make sure that the tab to format is not ticked and then off you go ...

be careful and make sure you do not tell the setup to format that partition ...

---

### Post by Scunge on 2008-08-25
I understand the idea of all users' data being under /home and in a separate partition, just for this sort of circumstance where a reinstallation is desired.

But...

What about user accounts themselves, I mean, the actual userIDs, groupIDs, passwords? They're in /etc somewhere I think, aren't they?

Surely in a complete system reinstallation, you'll end up with your initial adminey user only and so any other users created before will have lost access to their data, and their passwords will be reset if you recreate them?

And if you do recreate them, is it enough to simply create the new users in the same order as before, to get the same user IDs and group IDs, in order to restore correct permissions to existing /home files?

So, are there a list of files to save from the old install to make this process easy?

---

### Post by gatenby_jp on 2008-08-25
If you copy each of the /home/user1 ... /home/user2 etc folders into the /backup partition you have created.

Now do your your new install and create all your users. 
lets say you had two original users ... joe and jean you would now have /home/joe and /home/jean while in the /backup you would have folders joe and jean 

open a terminal and run the following command
sudo chown -R joe:joe /backup/joe
and sudo chown -R jean:jean /backup/jean

that will set all the uid and gids of those folders to the currently required ownerships of the new 
 system

You should have installed all the bits of software that you want the remembered data from before you copy from the /backup folders to the /home

you should of course have installed those pieces of software that have data in them before you copy the backup folders into /home

if you now reboot with the live cd and mount the various partition you can remove the newly created /home/joe and /home/jean folders ... then simply replace them with those from /backup ... now if you are using firefox for browsing and thunerbird for e-mail you will also have all your saved passwords and personalisations of firefox and thunderbird as well as all your past emails etc 

If you want to copy the users previous login passwords they were in /etc/shadow so you could copy this file into your /backup ... then simply replace the line for each user in your new /etc/shadow with the lines of the old /etc/shadow ... however i prefer not doing this and simply re-entering the correct password when I create the user

---

### Post by willthebold on 2008-08-25
Actually, I'm running two HDs so I'll just backup stuff to the other one, and install fresh on the one I'm booting to now. I just wondered if there was a way to avoid waiting for it to copy all my stuff. Oh well, I'll just occupy myself while I copy files. Thanks for the info about backing up user ids and whatnot. That's awesome.

---

