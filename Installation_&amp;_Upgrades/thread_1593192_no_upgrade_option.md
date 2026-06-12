---
title: "no upgrade option"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Mirrorboy on 2010-10-11
I'm running 10.04.1 and I want to upgrade to 10.10, but the option in update manager isn't showing up. I also ran "update-manager -d", but the option in that was for the RC. Any help?

---

### Post by solar george on 2010-10-11
By default the update manager in 10.04 will only show new LTS releases (the next will be 12.04) in order to make it show 10.10 as an option you must run update manager normally and click on settings in the bottom left corner. From the "Release Upgrades" drop down select Normal Releases then close the software sources window. Click reload in the update manager and you should have the option to upgrade.

---

### Post by Mirrorboy on 2010-10-11
Ok, I got that set. But now when I try to do the upgrade, it says "Cannot calculate upgrade" and something about broken packages. I've searched it up and did whatever it said to clean up the system and it didn't work. I honestly have no idea what's going on and it's driving me a little crazy. Any tips?

Also, can an upgrade be performed through the CD? I have the ISO file ready to burn, but I don't want to waste a CD if it won't work.

---

### Post by solar george on 2010-10-11
If you want to upgrade you'll need to fix whatever problem your having now - you can't realiably upgrade by any means unless your starting point is clean.
In any case you can only upgrade from the alternate cd not the ordinary desktop one.
Could you try and be a little more specific with the error messages and what you have tried to fix the problem.

---

### Post by Mirrorboy on 2010-10-11
The alternate CD install gave me the same error, so that doesn't matter anyway. The error is sort of vague. It said "An unresolvable problem occurred...you have held broken packages." Doesn't give any real information past that.

---

### Post by solar george on 2010-10-11
Can you post a list of any extra repos you've added e.g. ppas

---

### Post by Mirrorboy on 2010-10-11
Here's all I've got that I think would help. The first one is a screenshot of the error I keep getting, the other 2 are screenshots of my software sources setup.

---

### Post by solar george on 2010-10-11
I see you've removed the xorg-edgers ppa, did you run ppa-purge and downgrade all the packaged back to lucid's defaults?

---

### Post by Mirrorboy on 2010-10-11
Lucid was having trouble with the default graphics and I had to update them. Otherwise, the graphics would spaz out and self destruct in a way. As far as any commands and anything go, don't assume I know what you're talking about because I probably won't. I'm a very basic Linux user who needs all the answers and commands spoon fed to him. So if there's anything you feel I should do that would help, post the codes and what I'm supposed to do.

---

### Post by lechien73 on 2010-10-11
The error message says that you have "held broken packages".

Maybe to see what packages are on hold, you could type the following from a terminal window:

```
dpkg --get-selections | grep hold
```

That should give a list of all held packages, and then maybe we can see which ones are broken.

---

### Post by Mirrorboy on 2010-10-11
Nothing happens when I enter that into terminal. It just brings up another line as if nothing happened.

---

### Post by solar george on 2010-10-11
@lechien73
that won't work with the release upgrade process under any circumstances because it reverts any sources.list changes when it fails

OK so I assume that you still have the xorg-edgers drivers installed since you've not actually done anything about removing them. This would explain why you can't updgrade since they have to be removed before a release upgrade. (see [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa))
You'll need to re-enable that ppa, do an ordinay package upgrade then install ppa-purge and use it to remove the unofficial updates before updating.
```
sudo ppa-purge xorg-edgers
```

---

### Post by Mirrorboy on 2010-10-11
I re-enabled those 2 PPA's, but nothing came up in an update. I ran sudo apt-get update and sudo apt-get upgrade, but there weren't any updates. I also tried through the update manager and again got nothing. Just to see if it was already installed, I ran your code through terminal and it said command not found.

---

### Post by solar george on 2010-10-11
You need to install ppa-purge first, the upgrade was just to make sure your system would run ppa-purge correctly - it needs to be installed in addition to the upgrade.

---

### Post by Mirrorboy on 2010-10-11
That was it! I ran ppa-purge and it got rid of the problem right away. I have the upgrade going as we speak and there should hopefully be no more problems. Thanks a lot, SG, you've been a big help :)

---

### Post by spiralx on 2010-10-11
> By default the update manager in 10.04 will only show new LTS releases  (the next will be 12.04) in order to make it show 10.10 as an option you  must run update manager normally and click on settings in the bottom  left corner. From the "Release Upgrades" drop down select Normal  Releases then close the software sources window.
O. M. G.

What IS it about Linux and geek-world??  Do we all have to be Linux maestros with Ph.D's in the subject, just to explore options on a simple potential upgrade?

WHY couldn't the upgrade manager prompt the user when this happens?  Offer options?

And why can't the upgrade simply proceed, if you say "Yes", and if "broken packages", etc. are found, why can't it talk you through it, and offer you the option to cancel or proceed by deleting those packages?

Then you'd know what was going on, and have the control over what you are doing...

...surely?

Windows may be a lot of bad things, but user-friendly they ALWAYS get so right.

---

### Post by Slim Odds on 2010-10-11
> **spiralx said:**
> ...

Windows may be a lot of bad things, but user-friendly they ALWAYS get so right.

Apparently, you've never upgraded a Windows installation. There are a crap-load of things that can and will go wrong with any OS upgrade, especially if there are a lot of third party application installed. So get off your high horse or go to a Windows forum somewhere.

---

### Post by cariboo on 2010-10-11
Doesn't anybody actually read the release notes? it tells you how to do the upgrade. Seeing as nobody did. the correct way to upgrade is to press Alt-F2 and type:

> update-manager -d

then follow the prompts. 

The ppas will be disabled for the upgrade, and you will have to re-enable them after the upgrade is finished.

If you stick with the Ubuntu way of doing the upgrade you shouldn't run into any problems.

---

### Post by alexfish on 2010-10-11
Details upgrade from 10.04 to 10.10......(desktop edition)

[http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Read carefully all details

once commited

follow the prompts(read in detail before committing)

as said be patient (IE don't rush)

then hopefully you will have something like the screen shot

---

### Post by solar george on 2010-10-12
> Doesn't anybody actually read the release notes? it tells you how to do the upgrade. Seeing as nobody did. the correct way to upgrade is to press Alt-F2 and type:

Quote:
update-manager -d
then follow the prompts. 

The ppas will be disabled for the upgrade, and you will have to re-enable them after the upgrade is finished.

If you stick with the Ubuntu way of doing the upgrade you shouldn't run into any problems.
Perhaps you read the release/upgrade notes while they were still refering to the beta - the method currently recommended for the stable release is to change the update settings to notify of normal releases as opposed to just LTS ones.

Also wrt. ppas xorg-edgers is a special case and **must be ppa-purged** (see their launchpad page) before attempting release upgrades.

Finally I'm not really sure why people have felt the need to post general update instructions in a thread which has just sorted a special case upgrade.

---

### Post by Slim Odds on 2010-10-12
> **solar george said:**
> Perhaps you read the release/upgrade notes while they were still refering to the beta - the method currently recommended for the stable release is to change the update settings to notify of normal releases as opposed to just LTS ones.
...

An actual reference to this would be good.

But, apart from recommendations, the default behavior for an LTS release is to only look for the next LTS release as an upgrade option. This is defined by Canonical and not the user. Therefore, the use would have to manually change this. Most users are probably not aware of this default setting.

---

### Post by solar george on 2010-10-12
> **Slim Odds said:**
> An actual reference to this would be good.

But, apart from recommendations, the default behavior for an LTS release is to only look for the next LTS release as an upgrade option. This is defined by Canonical and not the user. Therefore, the use would have to manually change this. Most users are probably not aware of this default setting.

[https://help.ubuntu.com/community/MaverickUpgrades](https://help.ubuntu.com/community/MaverickUpgrades)
The upgrade notes, linked to from the various places on the website, explain what settings to change.

---

### Post by fast_ian on 2010-11-23
I had what appeared to be the same problem, and this thread was the top hit, so I'll add my recent 02c, FWIW:

- The release notes I read [ [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade) ] have no mention of changing the "default" in order for the upgrade to appear - The first I learnt of that was here.

However, even setting "Normal" under settings in the update-manager did not find the upgrade.

It did however work after I added the "-d" option.

HTH someone,
Cheers,
Ian

---

### Post by FrLarryDuff on 2011-01-12
Hey I was having the same problem trying to upgrade from 10.04 to 10.10. Changed the setting to "normal releases" and ran alt+f2 and then update-manager -d but to no avail. I then tried sudo update-manager -d from a terminal and hey presto! Hope this helps someone.

---

