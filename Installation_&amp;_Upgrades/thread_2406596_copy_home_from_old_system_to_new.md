---
title: "copy /home from old system to new"
date: 2018-11-22
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2018-11-22
well I finally got my "new" system beaten into submission. a Nice clean install of 18.04 on about 30gb, a SEPERATE /home partition (this is a big deal as inadvertantly mixing my root and /home has always caused me problems in the past)  and a dual install of Windows just in case.

but, how best to get my old /home files and folders over to the new system. is the command line approach outlined most places really necessary? 

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

for a relative novice it seems daunting. But when I just  copy my old /home files to a external HDD and then try to copy them into the new /home (while Live Booted), it fails on permission errorrs.

if you tell me there is no other good way, I will hunker down and work through the steps. but I am highly skeptical I will manage to make it work.

---

### Post by pjstock on 2018-11-22
Hmmm, though when actually logged into the new system I don't get the Permission Errors. Most files are copying just fine.
but I am sure I risk missing something.
what will I miss by doing this blunt force copy and paste.?

---

### Post by 1clue on 2018-11-22
This is tricky. 

Regular documents will copy right over. Simple single-file settings files will likely be fine too.

 The issue is with settings files in your $HOME directory. You will be copying old configurations (from your old system) onto new configurations (from the new install), and in many cases you'll have new settings files which didn't exist in the old sytem, old settings files that don't matter to the new system, and old versions of files which exist in both old and new.

In most cases when a new app with complex configuration (Firefox for example) notices config files from a prior version it will do an upgrade. But if you copy one group over the other, the app could get confused as to which version of which setting is what. I have had subtle unpleasant behaviors with that sort of thing in the past.

Then you get the situation where an old unused file is sitting around taking up disk space, when a clean upgrade would have removed the file.

I take settings app-by-app. In many cases it's better to reconfigure your new app with your favorite settings than it is to try to figure out what's misbehaving.

---

### Post by 1clue on 2018-11-22
Another thing, if your login name changed then you may get extra issues. Many apps configure login name or absolute path into the config file.

---

