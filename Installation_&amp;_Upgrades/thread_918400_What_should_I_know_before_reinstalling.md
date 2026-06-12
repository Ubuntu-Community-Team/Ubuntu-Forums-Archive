---
title: "What should I know before reinstalling?"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by Johnny K on 2008-09-12
It looks like I'm going to need to reinstall Ubuntu. I suffer from a [crippling bug]("http://ubuntuforums.org/showthread.php?p=5372744#post5372744") which seems to be a mystery to ubuntuforum users.

I've never reinstalled Ubuntu, what do I need to know?

Obviously all home folders can be restored after the install. Are there any other folders which I should restore after the install?

---

### Post by iaculallad on 2008-09-12
> **Johnny K said:**
> It looks like I'm going to need to reinstall Ubuntu. I suffer from a [crippling bug]("http://ubuntuforums.org/showthread.php?p=5372744#post5372744") which seems to be a mystery to ubuntuforum users.

I've never reinstalled Ubuntu, what do I need to know?

Obviously all home folders can be restored after the install. Are there any other folders which I should restore after the install?

I can't think of any folder for you to backup except your /home folder.

---

### Post by Neo_The_User on 2008-09-12
Make sure all your work is backed up (if any) on a different device. Happened to me once. :(

---

### Post by Herman on 2008-09-12
The other posters are right. Back up you entire /home/username directory, that should contain all of your personal files.
If you have any other users accounts in your computer, (if you share your computer with a friend or family member), back up their /home/username folder too, of course.

When you restore, you can obviously restore all of the normal files and folders like 'Documents', 'Music' and 'Videos' and so on.
Then, after you finish all the simple ones, just click 'View'-->'Show Hidden Files', and you will see hidden files and directories with names like '.evolution' and '.mozilla'. 
.evolution contians 'addressbook', 'calendar', 'mail', 'memos' and 'tasks'. All of those are simple to restore to your new operting system, you just paste them into your new /home/username/.evolution to overwrite the new empty directories fo the same name.
You have to configure Evolution first in the new system to have a new .evolution folder made for you first though.

Firefox used to be the same, I used to just copy the bookmarks file from somewhere deep within the .mozilla directory, but now there's an import wizard in Firefox, so it's best to use that. 
Actually, there's a new import wizard for Evolution too, but I'm a little old fashioned, I haven't used that yet, I still do it the old way. 
 
The rest depends on what software you use. 
.gpass is an important one for me because I use 'Password Manager', so that folder is vital as it contains all of my important password in encrypted form.
.tomboy will contain notes and reminders.
.shh is another one, because that contains my .ssh keys.
Important things like PGP anc RSA keys should already be backed up somewhere else and kept secure well before now anyway, of course. 
There may be many other hidden files and directories that are meaningless and can be made again. Most stuff you can leave behind. You'll know what it is you need when you see the names of the folders and files. Use your own good common sense and you'll be able to figure it out pretty easily. Just keep the backup for a while in case you forgot or overlooked anything. You can always go back to it to get something later.

One more thing you can back up if you want to save some time and bandwidth when you re-install is the contents of your /var/cache/apt/archives/ directory. That contains all of the up to date packages for all of your installed software, so you won't have to re-download it again. Only re-install that to another Ubuntu version that's the same as the old install though. If you had Ubuntu Hardy Heron you can use those packages in a new installation of Hardy Heron, but you probably can't use some of them in Intrepid Ibex, so don't try to use any of them, it isn't worth the risk.
EDIT: On second thought, after reading your previous thread, maybe you should not keep the same software packages in case those are the cause of your problems in the first place. Most people can carry their software forwards.

---

### Post by Neo_The_User on 2008-09-13
If you are like me and enjoy manually messing with your xorg.conf file, back up the xorg.conf file located in etc/X11/xorg.conf

---

### Post by Johnny K on 2008-09-13
> **Herman said:**
> The other posters are right. Back up you entire /home/username directory, that should contain all of your personal files.
If you have any other users accounts in your computer, (if you share your computer with a friend or family member), back up their /home/username folder too, of course.

When you restore, you can obviously restore all of the normal files and folders like 'Documents', 'Music' and 'Videos' and so on.
Then, after you finish all the simple ones, just click 'View'-->'Show Hidden Files', and you will see hidden files and directories with names like '.evolution' and '.mozilla'. 
.evolution contians 'addressbook', 'calendar', 'mail', 'memos' and 'tasks'. All of those are simple to restore to your new operting system, you just paste them into your new /home/username/.evolution to overwrite the new empty directories fo the same name.
You have to configure Evolution first in the new system to have a new .evolution folder made for you first though.

Firefox used to be the same, I used to just copy the bookmarks file from somewhere deep within the .mozilla directory, but now there's an import wizard in Firefox, so it's best to use that. 
Actually, there's a new import wizard for Evolution too, but I'm a little old fashioned, I haven't used that yet, I still do it the old way. 
 
The rest depends on what software you use. 
.gpass is an important one for me because I use 'Password Manager', so that folder is vital as it contains all of my important password in encrypted form.
.tomboy will contain notes and reminders.
.shh is another one, because that contains my .ssh keys.
Important things like PGP anc RSA keys should already be backed up somewhere else and kept secure well before now anyway, of course. 
There may be many other hidden files and directories that are meaningless and can be made again. Most stuff you can leave behind. You'll know what it is you need when you see the names of the folders and files. Use your own good common sense and you'll be able to figure it out pretty easily. Just keep the backup for a while in case you forgot or overlooked anything. You can always go back to it to get something later.

One more thing you can back up if you want to save some time and bandwidth when you re-install is the contents of your /var/cache/apt/archives/ directory. That contains all of the up to date packages for all of your installed software, so you won't have to re-download it again. Only re-install that to another Ubuntu version that's the same as the old install though. If you had Ubuntu Hardy Heron you can use those packages in a new installation of Hardy Heron, but you probably can't use some of them in Intrepid Ibex, so don't try to use any of them, it isn't worth the risk.
EDIT: On second thought, after reading your previous thread, maybe you should not keep the same software packages in case those are the cause of your problems in the first place. Most people can carry their software forwards.

Wow! Great information, I can't thank you enough!

I'll try it all out tomorrow. If I'm not back online by 5, send the search party!

---

