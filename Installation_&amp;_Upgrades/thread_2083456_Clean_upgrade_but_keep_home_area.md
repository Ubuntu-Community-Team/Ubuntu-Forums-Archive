---
title: "Clean upgrade but keep home area"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by inhumangeek on 2012-11-12
Evening,

I've been resisting upgrading from 11.10 (just because I wanted to do a clean install onto a new SSD but I was waiting for the prices to come down a bit first) but my hand has been forced and I went for the upgrade today, from 11.10 to 12.04. Anyway, this seems to have all gone a bit wrong, the graphical interface doesn't load upon boot, I've tried following the instructions from [here]("http://ubuntuforums.org/showthread.php?t=1743535") but with no success. 

Rather than spend hours trying to fix it, and as I wanted to upgrade clean anyway, I want to start again from scratch. Well, almost scratch... I had my system mounted on one HDD partition, and my home areas mounted on another partition. So ideally I would like to install 12.04 (or 12.10) _clean_ over the top of my old system but leave home in place, but I want to do it safely, as I believe there are lots of system/config files in /home/user that would need to be migrated to the new system? Plus I obviously want to keep all my documents, photos, etc. 

So what is the best way to do this? During the install do I simply choose to mount the home partition at /home and trust it to work itself out? Or do I leave /home in its default location, then somehow move it once everything is installed? (Presumably by booting to a live cd, removing all old hidden/system folders in home partition, moving new /home/user into home partition and editing fstab? This is where I get out of my depth) I have some Linux experience but I am not an expert, so (please!) keep any responses easy to understand!!

Finally, I don't have enough spare space anywhere to move everyone off the HDD before proceeding, but I do have everything backed up on an online backup service, but I would really rather avoid having to download all that again, so a fail safe mood would be appreciated. 

I have done a bit of a search for help but not even sure what a useful search string would be. 
Many thanks,
Paul

---

### Post by darkod on 2012-11-12
I have a separate /home also, and always do clean installs, never upgrades.

Yes, the correct way is to "use" the existing /home partition during the install. That way it will configure everything correctly without needing to mess around too much later.

You will have to use the manual partitioning (Something Else), and when you reach the partitioning step, select the /home partition and click the Change button below.
Now, this is VERY important: In the Use As field you HAVE to select the same filesystem that you currently have, for example ext4. Only in that case it can reuse it wothout formatting.
After you select the filesystem, for mount point select /home, and MAKE SURE the format box IS NOT selected (ticked).

Set up the root and swap partitions too, and off you go. Before you continue take a look at the partitions list and double check that formatting is not selected for the /home partition (there will be a mark next to the partitions that are selected for formatting. If /home is about to be formatted too, you know you did something wrong and don't continue with the process.

PS. Don't forget you have to create the same first user during the install as the one you had in your old system. If you have more than one user, you can create the others later. But create the first with the same username so that it matches the existing in /home.

---

### Post by inhumangeek on 2012-11-12
Thanks for the very quick response!

How can I tell for sure what filesystem it currently is? From a live USB, gparted declares it as ext4... I assume this must be correct. 

I will let you know how I get on on the other side..

---

### Post by darkod on 2012-11-12
Yes, it should be.

Another test, so you can see if it matches, in terminal run:
sudo blkid

That will show the UUID string and filesystem for all partitions.

---

### Post by inhumangeek on 2012-11-12
I simply can't believe how easy that was and how well it works. All my home area is in tact, everything seems to work how it should! I am still even logged in to ubuntuforums (on Chrome)!

Thanks very much!!

---

### Post by darkod on 2012-11-12
Wonderful, isn't it? Even your wallpaper is the same. Much better than dealing with failed upgrades. All settings that are kept under Home (and that means most of them), are there automatically.

Now you know how to do it in future, enjoy it. :)

---

### Post by inhumangeek on 2012-11-12
I will, and I won't be as hesitant to upgrade! 

Thanks again

---

