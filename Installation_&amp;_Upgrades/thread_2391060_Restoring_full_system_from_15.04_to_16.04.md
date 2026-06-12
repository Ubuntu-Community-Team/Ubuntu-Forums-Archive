---
title: "Restoring full system from 15.04 to 16.04"
date: 2018-05-05
forum: Installation &amp; Upgrades
---

### Post by trenza on 2018-05-05
I'm doing an OS upgrade for someone else's computer, and I'm trying to figure out the best way to restore all their files, programs, and settings. Unfortunately, because I'm upgrading from 15.04 which is EOL, I have to do a fresh instillation, and then restore from a backup. I've been doing some research on backup tools, and right now both Deja Dup and Clonezilla look like good options, but I'm also looking for suggestions. Is there an easy way for me to just back up the entire root folder, including all user's programs and configurations, and then just restore everything on a newer version of Ubuntu? What's the best way to go about this?
Thanks!

---

### Post by TheFu on 2018-05-05
That is not an option.   Compatible program versions change with every release, so trying to run programs built for 15.04 on a 16.04 will certainly have issues.

You can make a list of programs installed through the package manager on a running 15.04 system.  The list will include programs that weren't manually installed, which is less than ideal.  **dpkg --get-selections**  Newer releases have a tool called **apt-mark** - which can get just the manually installed packages. Check the manpage for option to do what you need, if it is available on 15.04.

And of course, all user settings are stored in each userid's HOME directory, so be certain to get those in the backup.

For normal desktop users, that should really be 98% of what they need. System settings are stored in /etc/, but normal end-users  don't touch those in a way that matters between releases. /etc/ is small, so backing it up isn't bad, just don't blindly restore anything from there into a new install.

Clonezilla and other imaging tools aren't really a good idea when you aren't trying to ... uh ... er ... clone a system.

Definitely use a backup tool and be certain it retains owner, group, permissions and ACLs for each file as they change over time.  Some popular backup tools require a Linux file system, so don't expect external NTFS storage to retain those things.

If I were doing this (1-time copy/backup then restore), I'd use rsync to get /etc/, /home/ and apt-mark (if it is supported) to make a list of manually installed programs in a file that was also stored in a HOME directory (so it would be restored with HOME directory data later.

With 16.04 and later, you might want to check out aptik.  It isn't really a backup tool, but the feature list does look nice for a system migration tool - which is really what you are hoping to accomplish.  At least that is what I believe you are asking. If not, please provide clarification.

And please be certain to explain LTS to the owner, so they are always moving from an LTS to LTS to LTS with their system updates.  9 months of support just isn't sufficient for most end-users.

---

