---
title: "initscripts, cupsys updates errors, no shutdown"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by RideTheLightning on 2007-12-04
I am running 64 bit Gutsy on a Sony Vaio laptop, Intel Core2 Duo (dual core) 1.8GHz processor, 2 GB of RAM, and dual boot with Vista.
As you read this, keep in mind that I have NO valuable data on Ubuntu, and the only things that I would want to keep are all the games I downloaded (not the games, but rather the list of games so I know which ones to download again).  So dangerous advice is welcome; I'm already considering a wipe of my Linux partitions and a fresh install of Gutsy, but I think the same errors might come up then, too, since I haven't actually learned anything about the errors.

When I open Update Manager, I receive the following error message:
Not all updates can be installed
"Run a partial upgrade, to install as many updates as possible.
This can be caused by:
A previous upgrade which didn't complete
Unofficial software packages not provided by Ubuntu
Normal changes of a pre-release version of Ubuntu"
with buttons "Partial Upgrade" and "Close".

The first on the list is true; my upgrade from Feisty to Gutsy (which occurred within a week after Gutsy was released, so a while ago) had some issues:
Some initscripts updates failed; I researched it a little earlier and found a sort of solution involving disabling it or them because sysvinit was the new version of it (my understanding was slightly better a few months ago).  Also, the same cupsys updates that fail now failed then, as well.  I was never able to find a solution for it.

The second on the list is very likely true; I installed a fair amount of stuff from the Ubuntu community.  However, I have seen no indication that what I installed is the problem (I haven't looked very hard, and I wouldn't know, but just to say that I haven't seen anything).

I don't believe the third is true.

If I choose Partial Upgrade, I receive the following error message:
"Could not calculate the upgrade
A unresolvable problem occurred while calculating the upgrade.
Please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport."

(I would do so, but I feel like it's something stupid I did to cause that.)
When I close that window it closes the Update Manager, and nothing else happens.

If I choose Close (instead of Partial Upgrade), I am told my system is up-to-date and I see no updates in the menu (I used to see grayed out choices).  If I close the Update Manager, nothing happens.
If I choose "Check" in the Update Manager, (well, this doesn't always happen, but) I got 24 updates to install.  I choose to install them, and all updates succeed except that I receive the following error:
"E: cupsys: subprocess post-installation script returned error exit status 1"
Looking around the forums I see that this particular error has occurred for many other people.
When I close the error box, the Update Manager appears again with the same "Not all updates can be installed" error from before.

So, the files from /var/log/dist-upgrade/ are attached (tar.gz, before tar the files are 620KB, before gzip the tar is 610k, all of the files inside the tar.gz are text).  I am afraid to attach a tar.gz because I'm not sure how you can trust the contents, but the attachment limit on a text file is 19.5 KB, and these are significantly larger than that.

Lastly, I cannot shut down (using the little red power button at the top right of a gnome desktop).  It appears to simply log off, though I'm not quite sure what it is doing.  I end up at the main login screen a second or two after selecting shut down.  I should note that shutting down worked fine until yesterday (a fresh batch of updates).
EDIT: On running "shutdown" in the terminal, I was informed that I had no command "shutdown", and it could be found in sysvinit.  I installed sysvinit and now shutdown works.

I'd be happy to test stuff and post the results.

Thanks in advance for the reply.

---

