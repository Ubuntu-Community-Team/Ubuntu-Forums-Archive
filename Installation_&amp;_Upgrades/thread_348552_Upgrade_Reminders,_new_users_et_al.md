---
title: "Upgrade Reminders, new users et al"
date: 2007-01-28
forum: Installation &amp; Upgrades
---

### Post by William Pickett on 2007-01-28
[SIZE="4"][/SIZE]

Hello Fellow Ubuntu users,

I wanted to share an item which I hope will help many to recover or prevent upgrade errors like I had the first time I did an Edgy upgrade:

Here are the steps I did this time which I believe I failed to do the first time, and now- it seems that I did something "right" because the desktop looks like a windows desktop- and that must be because of mods that have been requested which I did not see the first time I did Edgy upgrade- and why my xorg GUI failed as well. (first time not currently)

Before you begin, might be a good idea to do a backup on your files, sources list which I believe  you can find in the basic resources how to's- sorry I am new and do not recall the correct commands here, even though I did use these.


1) First, type gksudo gedit, which brings up the sources list. In every line which says Dapper or Breezy, if you still use that one, change word to Edgy. Then in the top of that screen click on "save" to save your changes. lower case is fine as well...

2) from command prompt type sudo apt-get update
3) type sudo apt-get upgrade
4 type sudo apt-get dist-upgrade
5) type sudo apt-get install
6 If at this point you lose the ability to login- example from my experience- about almost an hour or better later after all this finished compiling, I saw an icon top of screen alerting me to system upgrades available- so I clicked on it and of course it asked me for my password- which failed- reason (afterthought) that this operation failed is because the new updates had not read the old update info ref system user root- so I then found a site that said to do sudo -s -H and it will say Password: (here you type in the last known password that worked, in my experience) and then you find yourself as Root:(your user name) #~; which is what you want here [update040207]  $ indicates regular user but sudo allows you admin access, thanks to user post to clarify...(2)
7) So type again- (leave out sudo since you are root) apt-get update 
and this will take maybe another hour (was running older athlon 800 mhz).

8) You should watch all this because you'll see many fixes resolve themselves- example I had- was watching all the errors which I had- python/perl errors ref language [ Perl warning setting locale failed] these all and many more, which you will see as the compile continues, will be resolved. It was amazing to watch all the errors get fixed as the new routines were called from the updates currently available... pretty neat,  ... now if we can just take back control of our government- and fix That Mess- hey- what a concept.

If I can help, email me [email]wkpickett0154@comcast.net[/email] subj: Ubuntu Users Questions.

William Pickett

---

### Post by bapoumba on 2007-01-29
Hello,
I just wanted to point a couple  things out :
> **William Pickett said:**
> [SIZE="4"][/SIZE]
1) First, type sudo gedit
**gksudo gedit**

> **William Pickett said:**
> [SIZE="4"][/SIZE]
1) First, type sudo gedit, which brings up the sources list. In every line which says Dapper or Breezy, if you still use that one, change word to Edgy. 
Not sure going from breezy to edgy is such a good idea ;)

> **William Pickett said:**
> [SIZE="4"][/SIZE]
 then you find yourself as Root:(your user name) $~; which is what you want here

Root prompt looks like this : #.
$ is when you are logged as a regular user.

---

