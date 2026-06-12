---
title: "Should you Partial Upgrade?"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by jblackhall on 2008-10-09
I see a lot of topics in here talking about how upgrades broke this or that feature.  I upgraded to Intrepid last night and I was reminded about the Partial Upgrade feature.  I ran Hardy since in beta and I remember being confused about the "Partial Upgrade".  Someone please correct me if I'm wrong, but I thought there is only 1 instance when you *ever* want to run Partial Upgrade without breaking anything: if you can *confirm* that a particular package is *supposed to be removed* (like it's deprecated) by Ubuntu.  

This is how I seem to remember things.  If a package is taking a particularly long time to build (so it's not ready to be upgraded yet), it will show up as "not there".  When you go to run Partial Upgrade, it will remove any packages from your system that are "not there" in Update Manager.  This can break stuff if Ubuntu starts removing stuff from your machine that you need just because it hasn't finished building yet.

Now I know updates can definitely cause bugs and make stuff not work, but I recall having fewer issues in the Hardy Beta by never doing a Partial Upgrade unless I knew that the only packages going to be removed were ones that were supposed to be removed.  

Am I correct here?  Do you (should you?) do Partial Upgrades every time you update?

---

### Post by FuturePilot on 2008-10-09
No you should not. This message is usually caused because a package needs to be removed. Update Manager cannot remove packages, only install them. Therefore, if a package needs to be removed Update Manager will give this error. The best solution to this is to use Synaptic to do the updates if you happen to see this message. It will be able to handle the removal of the packages that need to be removed. Doing a partial upgrade could possibly leave you with a broken system.

---

### Post by philinux on 2008-10-09
+1 for no.

During the alpha/beta/rc phase occasionally some apps need to be removed before the new version can be installed. Unfortunately update manager can remove apps without installing their replacement. One year it removed itself!

Cancel the partial then update then use synaptic channel "upgradable(upstream)". Mark the upgrades then click apply.

---

### Post by jblackhall on 2008-10-09
> **FuturePilot said:**
> No you should not. This message is usually caused because a package needs to be removed. Update Manager cannot remove packages, only install them. Therefore, if a package needs to be removed Update Manager will give this error. The best solution to this is to use Synaptic to do the updates if you happen to see this message. It will be able to handle the removal of the packages that need to be removed. Doing a partial upgrade could possibly leave you with a broken system.

Sometimes packages *do* need to be removed, even at this stage of the game.  But "Partial Upgrade" will allow for removal of packages just like Synaptic will.  My point is, sometimes this is actually supposed to happen, and many more times (at this stage in the game) it is NOT.  Using Synaptic won't resolve the issue if they're NOT supposed to be removed.  The reasoning (as I explained above) for why Synaptic or Partial Upgrade would want to remove a package is that the upgrade notification has appeared but not the actual upgrade (i.e. it hasn't finished building).

So for example, as I type this, both Partial Upgrade and Synaptic want to remove "compiz" and "compiz-fusion-plugins-extra", neither of which it sounds like I want to remove.  I assume this is due to the fact that the packages haven't been fully built yet.

Is this information correct?

---

### Post by FuturePilot on 2008-10-09
> **jblackhall said:**
> Sometimes packages *do* need to be removed, even at this stage of the game.  But "Partial Upgrade" will allow for removal of packages just like Synaptic will.  My point is, sometimes this is actually supposed to happen, and many more times (at this stage in the game) it is NOT.  Using Synaptic won't resolve the issue if they're NOT supposed to be removed.  The reasoning (as I explained above) for why Synaptic or Partial Upgrade would want to remove a package is that the upgrade notification has appeared but not the actual upgrade (i.e. it hasn't finished building).

So for example, as I type this, both Partial Upgrade and Synaptic want to remove "compiz" and "compiz-fusion-plugins-extra", neither of which it sounds like I want to remove.  I assume this is due to the fact that the packages haven't been fully built yet.

Is this information correct?
Yes that could be another possible cause, in which case you should still not do a partial upgrade. If there are packages that haven't been built yet it will most likely cause broken packages due to missing dependencies. I've seen partial upgrades want to remove half the system before because of a missing package or incorrect version in the repos.

---

### Post by forger on 2008-10-09
you should not do upgrades through the update-manager yet, I suggest using aptitude or apt-get
```
sudo aptitude update; sudo aptitude safe-upgrade
```
..or..
```
sudo apt-get update; sudo apt-get upgrade
```

This way, you can see *exactly* which packages you can safely install or not. Some packages will be asked to be removed, so use the letter "Y" and the letter "N" wisely :)

---

### Post by jblackhall on 2008-10-09
> **FuturePilot said:**
> Yes that could be another possible cause, in which case you should still not do a partial upgrade. If there are packages that haven't been built yet it will most likely cause broken packages due to missing dependencies. I've seen partial upgrades want to remove half the system before because of a missing package or incorrect version in the repos.

Right, so really there's no difference between doing a partial upgrade and using Synaptic and doing Mark All Upgrades.  The only difference that I see is that the Partial Upgrade message lets me know that "hey, something's not ready to upgrade right now.  maybe i should just click 'close' and install things that aren't greyed out (and thus can be safely updated)"

I don't like using Synaptic because all it does is tell you what's being removed, not whether or not it's a good idea to remove it (no "partial upgrade" warning message).  

So I guess my question is, should we be encouraging people (who aren't 100% sure what should be removed) to use only use Update Manager for updates and to only run Partial Upgrade when they're sure that the only things being removed are those that are *supposed to be*?

I guess I feel like that technique would solve a lot of people a lot of headaches in running the pre-releases.

---

### Post by danf_1979 on 2008-10-09
safe-upgrade will not uninstall packages. Try using full-upgrade.

```

$ man aptitude 
$ sudo aptitude update && sudo aptitude full-upgrade

```

full-upgrade will complete all changes, install new packages and/or uninstall them if necessary. Keep in mind that this is dangerous, so don't accept the changes without reviewing them and being completely sure they will not harm your system in a terrible way.

Aptitude's log is in /var/log/aptitude

I almost never use synaptic or update manager. Aptitude is just way better and gives you a lot more control. Read the manual, and use it. If your get used to it, you won't regret it.

---

### Post by jblackhall on 2008-10-09
> **danf_1979 said:**
> safe-upgrade will not uninstall packages. Try using full-upgrade.

```

$ man aptitude 
$ sudo aptitude update && sudo aptitude full-upgrade

```

full-upgrade will complete all changes, install new packages and/or uninstall them if necessary. Keep in mind that this is dangerous, so don't accept the changes without reviewing them and being completely sure they will not harm your system in a terrible way.

Right, but how can I be sure what I want to remove and what I don't want to remove?  Sometimes it's obvious, but many times it isn't.  And especially at this point in the release cycle, there are many more packages I DON'T want to remove than those I do (because they're deprecated).  Running something like full-upgrade is going to cause many more problems than it's worth if you're not 100% sure what you're doing.

---

### Post by philinux on 2008-10-09
> **jblackhall said:**
> Right, so really there's no difference between doing a partial upgrade and using Synaptic and doing Mark All Upgrades.  The only difference that I see is that the Partial Upgrade message lets me know that "hey, something's not ready to upgrade right now.  maybe i should just click 'close' and install things that aren't greyed out (and thus can be safely updated)"

I don't like using Synaptic because all it does is tell you what's being removed, not whether or not it's a good idea to remove it (no "partial upgrade" warning message).  

So I guess my question is, should we be encouraging people (who aren't 100% sure what should be removed) to use only use Update Manager for updates and to only run Partial Upgrade when they're sure that the only things being removed are those that are *supposed to be*?

I guess I feel like that technique would solve a lot of people a lot of headaches in running the pre-releases.

Within the last few updates I cancelled all the partials and then let update manager update. When I used synaptic it told me what needed to removed and what was going to installed. Usually an older version being replaced with a new. This works for me and not borked my system. As usual in this game there is more than one way.

---

### Post by forger on 2008-10-09
well there are two kinds of partial upgrades:
1) the ones that tell you to remove stuff that were dependencies of other packages and not any longer.
2) the ones that in the development release, but their dependencies haven't been built/compiled/pushed to the repositories yet. These are the dangerous ones.

That's why I told you to use apt-get or aptitude, you'll get warnings if the dependencies aren't met.. if you see anything removing ubuntu-*, it's usually bad, **unless** you are customizing your installation and removing programs you don't use in order to minimize your operating system resources (not recommended while in development, you could end up with a lot of unused packages that were dependencies and in future releases weren't removed).

---

### Post by danf_1979 on 2008-10-09
> **jblackhall said:**
> Right, but how can I be sure what I want to remove and what I don't want to remove?  Sometimes it's obvious, but many times it isn't.  And especially at this point in the release cycle, there are many more packages I DON'T want to remove than those I do (because they're deprecated).  Running something like full-upgrade is going to cause many more problems than it's worth if you're not 100% sure what you're doing.

I almost everytime use full-upgrade, unless I see problems. The 3 most common problems:

a) Some core package is going to be removed, and so the uninstall package list is huge (bad thing).
b) There are dependency problems and some package is going to be removed, but it shouldn't (like gimp for example).
c) Unmet dependencies (not that bad), most probably aptitude will not touch it. If the situation is very bad, it may attempt to remove the package, or many packages depending on which package is going to be uninstalled. 

In this cases, just run aptitude with safe-upgrade option, and wait a day or two. Most probably the devs will fix the issue, specially in this cases, since the problem are dependencies.

Ofcourse you can always use "show" option in aptitude to read what a package is used for, and its dependencies. That way you can judge better if what you're seeing is supposed to be "normal"

```

$ aptitude show some_package_here

```

Normal stuff are packages being replaced, upgraded, and sometimes dropped. If you feel that you can damage your system, you can always post in the forums :)

---

### Post by jblackhall on 2008-10-09
> **philinux said:**
> When I used synaptic it told me what needed to removed and what was going to installed. Usually an older version being replaced with a new.

You say Synaptic told you what "needed to be" removed and upgraded/installed.  As I stated above, Synaptic just told me I "needed to" remove compiz and compiz-fusion-plugins-extra (presumably b/c they haven't finished building).  I definitely do NOT want to remove either of those.  

I guess I just feel like some people blindly click "Mark All Upgrades" in Synaptic or "Partial Upgrade" in Update Manager without fully knowing what they're doing.  Then they're system gets screwed up.  Now there are definitely bugs in these beta releases, but these things aren't really bugs.  They're just people removing packages that they shouldn't be.  I'm just trying to come up with a way to help them bork their system as little as possible :)

---

### Post by jblackhall on 2008-10-09
@danf_1979, thanks I didn't know that command.  That's useful.

@forger and @danf_1979, Thanks for the input.  I just feel like looking at a list of depends is a cumbersome way to go about doing daily updates.

I guess ideally Update Manager would handle all of this better so that only things that are verified to be removed would ever actual be removed during updates and things that haven't finished building yet would never show up until they did.

---

### Post by psyke83 on 2008-10-09
Let's put it this way: if you're unsure enough to *ask* if you should do a Partial Upgrade, don't do it!

I got disturbed when a user said that "the Updater told me to do a Partial Upgrade" - you're not being "told" to do the operation, you're being warned of the danger of that operation. Perhaps we need to clarify the language of the warning notification.

If you allowed a Partial Upgrade today, you would reboot into a desktop without compiz properly installed (your desktop would function, sans a window decorator running). When we move beyond beta territory, in 95% of cases it's a bad idea to do a Partial Upgrade.

---

### Post by zoomy942 on 2008-10-09
i just did a fresh install and am doing the partial upgrade.

it only wants to remove Gimp, everything else is an upgrade.  no harm done.

---

### Post by Sef on 2008-10-09
There is nothing wrong with doing a partial upgrade.   Like upgrading, it can crash your system, but that is not likely.

---

### Post by drobvice on 2008-10-10
I just did a partial upgrade and now my laptop fan is running full blast.

---

### Post by jblackhall on 2008-10-10
> **Sef said:**
> There is nothing wrong with doing a partial upgrade.   Like upgrading, it can crash your system, but that is not likely.

I beg to differ.  Look around this forum.  A number of topics are started because people do a partial upgrade (or upgrade through Synaptic and don't pay attention to what's being removed) and it removes huge packages (like compiz or ubuntu-desktop) because they're still building and they lose a big part of their system.  As was stated in this thread, it can be done, but you should probably make darn sure you know what's being removed because it hasn't finished building.  Like zoomy942 said, if you know what's being removed and you can live without it for a day or two, then go ahead and do it.  But if you don't know what you're removing (and you're not sure if it's supposed to be removed, which usually it isn't), it's probably a bad idea.

---

### Post by philinux on 2008-10-10
> **jblackhall said:**
> You say Synaptic told you what "needed to be" removed and upgraded/installed.  As I stated above, Synaptic just told me I "needed to" remove compiz and compiz-fusion-plugins-extra (presumably b/c they haven't finished building).  I definitely do NOT want to remove either of those.  

I guess I just feel like some people blindly click "Mark All Upgrades" in Synaptic or "Partial Upgrade" in Update Manager without fully knowing what they're doing.  Then they're system gets screwed up.  Now there are definitely bugs in these beta releases, but these things aren't really bugs.  They're just people removing packages that they shouldn't be.  I'm just trying to come up with a way to help them bork their system as little as possible :)

Correct so if you dont like what synaptic offers you say no. Case in point this aft see this thread. Partial would have borked your system. [http://ubuntuforums.org/showthread.php?t=943370](http://ubuntuforums.org/showthread.php?t=943370)
Waiting for the packages to be released sorted it eventually. Sometimes we must be patient.

---

### Post by solitaire on 2008-10-10
I personaly hate Synaptic for doing upgrades / updates! it's too easy to click through the message saying it's going to remove all Gnome related apps like the desktop (Happened to me with 7:10 when i tried to remove flash!).

I use 
```

sudo apt-get update
sudo apt-get upgrade

```If it's just installing things i let it go on it's way and update. If there is anything to be removed I say no and run Update-manager to see info on what's getting installed / removed before i run it.

---

