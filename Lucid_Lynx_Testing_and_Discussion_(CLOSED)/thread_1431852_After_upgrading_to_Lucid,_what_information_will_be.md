---
title: "After upgrading to Lucid, what information will be lost?"
date: 2010-03-17
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by auh2o on 2010-03-17
The day is drawing closer when I will be notified in the 9.10 Update Manager that Lucid is available as an upgrade. I came to Ubuntu during Karmic and thus have never upgraded to a new version before. That's why I would like to have it made clear beforehand exactly what will need to be reconfigured after the upgrade is done.

I have ascertained that all PPAs that I have manually added to the Software Sources (and they are quite a few) will be gone after upgrading, so I will have to enter those again. That of course make sense since they all point to Karmic repositories. But are there anything else I should know about and be prepared to configure again after an upgrade? Custom themes, network & VPN settings, manually installed applications, etcetera etcetera - will it all still be there and working after an upgrade? I will of course back everything up in advance, but it doesn't hurt to know what to be prepared for.

---

### Post by YannBuntu on 2010-03-17
Hello
First backup your data (/home ..) on an external drive. Then before upgrading to Lucid, burn a Lucid live-cd and try it in "live-session".
This should limit the risks.

Regarding your answer, there might be surprises, but generally all official software keep their settings.

You will have to reinstall your non-official software (PPA..), but it is not a big deal.

In case of problem with Lucid you will have your saved data , so that you can reinstall Karmic and put back your /home in it.

---

### Post by ajgreeny on 2010-03-17
I have seen and heard that it is best to either disable the ppa repos before doing the upgrade, or remove them completely from the sources.list file(s) that you are using.

---

### Post by auh2o on 2010-03-17
> **YannBuntu said:**
> Hello
First backup your data (/home ..) on an external drive. Then before upgrading to Lucid, burn a Lucid live-cd and try it in "live-session".
This should limit the risks.

Regarding your answer, there might be surprises, but generally all official software keep their settings.

You will have to reinstall your non-official software (PPA..), but it is not a big deal.

In case of problem with Lucid you will have your saved data , so that you can reinstall Karmic and put back your /home in it.

Thanks for your reply. I'll follow your advice. I will have to reinstall everything installed from 3rd party PPAs altogether, huh? That's something I didn't know, so it's good you told me! But no, I guess it's not too big a deal. Because all configuration files will  still be in my backed up /home folder, right?

> **ajgreeny said:**
> I have seen and heard that it is best to either  disable the ppa repos before doing the upgrade, or remove them  completely from the sources.list file(s) that you are using.

Thanks, I'll make a note to do that.

---

### Post by seeker5528 on 2010-03-18
> **auh2o said:**
> Thanks for your reply. I'll follow your advice. I will have to reinstall everything installed from 3rd party PPAs altogether, huh?

Removing/disabling the PPAs doesn't remove the software provided by those PPAs. If you choose not to get rid of the obsolete/locally installed packages and there are no dependency issues that trigger their removal they will be kept.

If you have done the sane thing and have a seperate file for each PPA in '/etc/apt/sources.list.d/' for each of the PPAs as opposed to adding them all to '/etc/apt/sources.list', for most of the PPAs it shouldn't be that big of a deal to edit these files to point to the Lucid stuff then and rename them to make the PPAs active again.

Depending on what you have installed, it does increase the risk of something being un-handled during the upgrade that may cause problems, in particular if you choose not to get rid of obsolete stuff. 

If you have a lot of stuff from PPAs it is a pretty safe bet that even if you choose to keep obsolete packages during the upgrade some of the stuff will be removed during the upgrade, but on the other side of the coin even you don't have anything from PPAs there always seems to be something that you have to re-install after an upgrade. PPAs or no PPAs, the more stuff you have installed beyond what's included in the basic install, the more likely it is you will have to re-install something after the upgrade.

Later, Seeker

---

### Post by NCLI on 2010-03-18
Generally, an upgrade is very safe. I've never lost any data during one, though, as always when making big changes to your system, taking a backup of your /home is a good idea. Not a necessity, just a good idea. 

The software you've installed from PPAs will be kept in most cases, and the PPAs themselves will just have to be re-enabled.

---

### Post by cariboo on 2010-03-18
I just finished upgrading from Karmic to Lucid. The first thing I did was make sure Karmic was fully up-to-date, next I disabled all the ppa's, then I ran:

```
update-manager -d
```

and selected to upgrade to the next version. It wasn't quite painless, but pretty close, aside from the 1866 packages that were downloaded.

Make sure you run:

```
apt-get clean
```

when done, as it cleared up about 2Gb of space on my / partition.

---

### Post by YannBuntu on 2010-03-24
@auh2o: please wait the final Lucid version before upgrading. The procedure that cariboo907 gives will give you an unstable version (currently beta).

---

### Post by emarkay on 2010-03-24
Even with a backup, some configs and operations (button position, for example) will be different, so it's best to not only have a physical backup, but know what you have changed!

I have a document I use that I use for reinstalls, but also applicable for updates, with all my personal preferences and settings, etc.

---

