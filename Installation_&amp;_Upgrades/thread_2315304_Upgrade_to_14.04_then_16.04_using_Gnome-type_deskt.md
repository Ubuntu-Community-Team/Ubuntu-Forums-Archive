---
title: "Upgrade to 14.04 then 16.04 using Gnome-type desktop?"
date: 2016-02-27
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2016-02-27
I am currently running 12.04 (configured to not show Unity) on several 64 bit computers. It is now time to upgrade to 14.04 prior to a move to 16.04 (after it has seasoned a few months). I have not already gone to 14.04 because I strongly prefer the old gnome style desktop and I remember that the process of upgrading and hiding Unity was time consuming.

FWIW, my \home directory is on a second drive. I also recall that setting that up, creating a tarball from the current \home and then successfully (i.e., dealing with permissions) moving that to the upgrade is also a bit complicated (for me) and time consuming.

I am out of the loop with respect to where Ubuntu is now with respect to Unity/Gnome Fallback/Flashback/etc so I am asking for guidance concerning how I might best accomplish the above while maintaining a gnome type environment. I believe there are one or more gnome offshoots, but I would prefer to stay with the mainstream LTS, just avoiding Unity and using a Gnome-type desktop. Any ideas welcome.

---

### Post by T.J. on 2016-02-27
I would advise against doing an "in place" upgrade using a version of Ubuntu that is 4 years old.  Not only is it extra work for you, it is likely to break.  I would simply replace 12.04 with a fresh install of 16.04 when it becomes available. Just make sure to backup your data for safety, and install manually.  Do not  format your /home partition, but tell the new install to mount it as /home, and you should be fine.  You might need to reset permissions on your /home/<username> directory, and clean out some old config files in your home directory for the updated Gnome to start, but that is a 5-10 minute fix. If you need more information on how to handle a manual install, please feel free to ask. I'm happy to be of service.

If you prefer the old Gnome - that is version 2, try the Mate Desktop, that is Ubuntu Mate: [https://ubuntu-mate.org/](https://ubuntu-mate.org/).  Mate is just an updated version of Gnome 2.

---

### Post by X-RED_Tech on 2016-02-27
+1 to a fresh install.

---

### Post by oldfred on 2016-02-27
I keep all data in separate /mnt/data partition, so then my / (root) partition can be smaller like 25GB.
Then I add another 25GB for new / and do a new install. Then I can test changes & make sure I have reconfigured to match old install.
I do export list of installed applications to reinstall and script most configurations. In your case just mounting /home but NOT formatting during install with Something Else should preserve your settings.

I am running flashback/fallback/gnome-panel or whatever its name is today following kansasnoob's instructions. I do have an install of 16.04, but have not installed gnome-panel, yet.

 gnome3 classic similar to old gnome2
sudo apt-get install gnome-panel
On login screen click on cog-wheel/star and choose 

        Kansasnoob on flashback/fallback in Saucy, Quantal and Raring
[http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225](http://ubuntuforums.org/showthread.php?t=1966370&p=12857225#post12857225)
Sixth, if you begin with an installation of Ubuntu GNOME, you'll find a login option for GNOME Classic but it should NOT be confused with the older classic/fallback/flashback sessions! The new GNOME Classic session truly is GNOME Shell with some cherry-picked extensions added to provide a "classic" look but it is NOT configurable in the same way as "Flashback"!

---

### Post by kansasnoob on 2016-02-27
The flashback session(s) are available in Trusty (14.04):

[http://ubuntuforums.org/showthread.php?t=2220264](http://ubuntuforums.org/showthread.php?t=2220264)

And they will be in Xenial (16.04):

[http://ubuntuforums.org/showthread.php?t=2302432](http://ubuntuforums.org/showthread.php?t=2302432)

The flashback w/metacity session is used by Edubuntu for LTSP installs so it's officially supported in LTS versions for 5 years. So Precise is good until April 2017, Trusty until April 2019, and Xenial until April 2021.

There have been changes in settings as GNOME themselves keeps changing (and sometimes deprecating) things in gsettings. These "changes" seem to result in problems with release upgrades causing end users to pull their hair out trying to wipe out the old, now defunct settings and then applying the proper new settings. I recently tested Trusty -> Xenial upgrades in preparation for Ubuntu's flavors Beta 1 and they fail:

[https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1549067)

I'd bet they'll get that fixed by April when Xenial is released but in general release upgrades are fraught with problems. So, at the very least, a person should always plan on having a broken system afterwards. That way you'll be prepared just in case re-installation is needed. If you don't have a full external backup of all your data you'll be doing yourself a favor by creating one anyway.

If Ubuntu is the only OS installed the live DVD/USB also offers an upgrade that I personally find to be much less fraught with problems, but even that is NOT fool proof and the older Trusty images had a bug that resulted in data loss using the early 14.04 and 14.04.1 images:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

I will be testing Precise -> Xenial upgrades using the live DVD when Xenial Beta 2 approaches just to see what blows up because I like to blow things up :twisted:

So the safe bet is to always create a full backup on some type of external media before attempting a release upgrade or reinstalling. It's like insurance. If you have it you'll seldom (or never) need it, but the moment you don't something will go wrong!

---

### Post by oldfred on 2016-02-27
> So the safe bet is to always create a full backup on some type of  external media before attempting a release upgrade or reinstalling.

The ghost in the computer knows if you have a backup. If you have one it does not create problems on changes, but if you do not have those backups, it knows and creates all sorts of issues. It can even make you type incorrect commands. :)

---

### Post by kansasnoob on 2016-02-27
> **oldfred said:**
> The ghost in the computer knows if you have a backup. If you have one it does not create problems on changes, but if you do not have those backups, it knows and creates all sorts of issues. It can even make you type incorrect commands. :)

I'm anal about backups :D I use external USB hard drives for backups which get stored in anti-static bags before being placed in Tupperware, and then they go in my gun safe (even though I no longer have any guns). But I've also lost stuff in the past to flood, fire, and a malicious ex :(

---

### Post by grahammechanical on 2016-02-27
In 12.04 it was Gnome Fall-back. In 14.04 it is Gnome Flashback. I am not certain that upgrading 12.04 to 14.04 will also upgrade Fallback to Flashback. If you did not uninstall Unity then uninstall Fallback and then install Flashback when you are at 14.04 or 16.04

If you are going to do a fresh install of either 14.04 or 16.04 then do not expect the default install to include Flashback. It has to be installed afterwards. If you use the Something Else option and do not format the /home partition (which is the right way to do this) then you will still have the old configuration files from Fallback and they may not be compatible with Flashback. Another reason to uninstall Fallback prior to changing to newer release.

When upgrading to a new release (as opposed to fresh install) we should revert the desktop to the default state as far as possible and should revert to using an open source video driver. Remember, the upgrade scripts are not designed to take into account all the variations that users do to the desktop.

Regards.

---

### Post by Odyssey1942 on 2016-02-28
Very helpful replies, thanks. Here is my idea at this stage (but subject to complete revision as better ideas might emerge). I don't trust upgrades and always start with a tarball of my /home) put a third drive for safety). My linux experience is limited and my memory even more limited, so will probably look for guidance also on this as process.

Next is to do a clean install of 14.04 now (16.04 in a few months while I stil can remember most of what I have to relearn now.)

Before commencing, I need to decide on the distro to use. I am currently using mainstream Ubuntu 12.04 which I was able to make look and work the way I want it: Task bar at top and at bottom and a clean (no unity bar) desktop allowing me to put files and folders on it grouped to my convenience. (If someone wants to see a screenshot, I will provide but will appreciate a reminder on how to take one.)

The single most important productivity tool on my computer is the several workspaces (eight in my case) at the right side of the bottom taskbar. This is an absolute must for me.

So if I can just go to bog-standard Ubuntu 14.04 and do the same mods as before (which I can also provide if any interest), that is one option. I am unsure what OldFred is using > I am running flashback/fallback/gnome-panel or whatever its name is today following kansasnoob's instructions but the next line > gnome3 classic similar to old gnome2 got my interest because I think this might be the sort of desktop I use and want. Fred, clarification as to what is the starting package and what "kansasnoob's instructions" actually are would be appreciated.

Graham, does my setup sound like what Gnome Flashback will provide?

If above confusing, happy to clarify. Thanks for your continued interest.

Edit: I just went back to the thread to look at something and found kansasnoob's first post which I completely missed in my initial reading of the replies this morning. May say something about being out too late last night, but reason is much more mundane. Anyway am now reading through the links and will comment further as appropriate afterward. Apology to kn.

---

### Post by Odyssey1942 on 2016-02-28
Wasn't difficult to take. Challenge was to get it into this thread.

[ATTACH=CONFIG]267572[/ATTACH]

---

### Post by Odyssey1942 on 2016-02-28
OK, I think T.J. nailed it. Have been testing Ubuntu Mate 14.04 for last two hours. It seems to incorporate natively all the features that I want, most of which previously needed to be manually and laboriously installed in bog-standard Ubunutu.

Thanks all.

OK to close this thread as solved.

.

---

