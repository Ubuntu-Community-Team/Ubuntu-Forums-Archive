---
title: "Preparation for Dappper Install"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by xtacocorex on 2006-05-22
When Dapper becomes stable, I'm going to jump on the install, but I have a  question I would like answered beforehand to fully prepare myself and provide reassurance for what I plan on doing.

I have /home and /opt on separate partitions that will not be reformatted. When I install Dapper, I will reformat / and lose all my files there. If I make my user during the install, will it try to rewrite over my home directory or go with it? 

Otherwise I would create another user, then go into CLI and add myself that way pointing to the home directory that is already there for me.

---

### Post by Sef on 2006-05-22
> If I make my user during the install, will it try to rewrite over my home directory or go with it? 

Are you doing a dist-upgrade or a clean install (from a cd)?

---

### Post by xtacocorex on 2006-05-22
Forgot to put that down, it'd be a clean install. 

I tried to use the new update manager the other day and it looked like it was going to break my system so I didn't do it.

---

### Post by Sef on 2006-05-22
If you do a clean install. your home and opt partitions should be ok.  However, **back up** your data first.  On occassion, your home partition can be lost, and the data with it.

---

### Post by xtacocorex on 2006-05-22
Will the user creation mess stuff up if I use my username and have it already have the directory there?

---

### Post by Nonno Bassotto on 2006-05-23
For me it worked well. I did a clean (cd) install of Dapper over Hoary.
I created the user I had before. I lost no data, and every settings was kept. Of course I had to reinstall some programs, but when they installed, they kept the same settings as before. For example I had my bookmarks, themes and extensions on Firefox, and my contacts on aMSN, Skype and XChat, my gDesklets where set as before and so on. Of course also my themes, and everything I can think of was kept.
BUT always do a backup before doing this. Moreover, you may consider backup of your settings also (they all are in home in hidden folders and files).

---

### Post by xtacocorex on 2006-05-23
Thanks for the reassurance. I plan on doing hefty backups to cd's since my backup script freezes my computer for odd reasons.

---

### Post by Morrolan on 2006-05-25
What does your backup script look like?  I have a very simple (self-written) bash backup script that uses tar that works like a charm, and i'd be glad to post it if it helps.

I backup to an external HD mounted at /media/DWORKIN/ , but you can always change that to wherever you want or I can make it interactive so that you can specify it as a variable on the command line?

It's gonna be easier than a whole bunch of CD's mate, that's for sure!

---

### Post by bluenova on 2006-05-25
Hi Morrolan,

I'd like to see your backup script.

---

### Post by Sef on 2006-05-25
> For me it worked well. I did a clean (cd) install of Dapper over Hoary.

If you are skipping a version, do a clean install.  If you do a dist-upgrade, you will break the system.

---

### Post by xtacocorex on 2006-05-25
@Morrolan:
Here is my backup script, it is also in bash and then creates .tar.gz of the directory you want archived depending on command line options. It works, but my ignores are off a bit I think so it's pulling in some of the stuff that I don't want. I haven't had time to fully mess with it, but I plan on doing so next week before I upgrade.

I have it set up to display the usage if there are no arguments and if you look at the script, the section that is user modifiable is labeled.

The random freezes are due to my laptop overheating since Dell designed the heat sink with no regard to aerodynamics.

I like to make things fairly complex since I'm an engineer, but feel free to use it and/or modify it, I put it under the GPL. Definitely let me know if you have any suggestions for it.

---

