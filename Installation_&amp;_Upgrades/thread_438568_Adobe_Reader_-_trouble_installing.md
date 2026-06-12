---
title: "Adobe Reader - trouble installing"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by docmeister53 on 2007-05-09
I am new to Ubuntu and am trying to install Adobe Reader using the install program in Gedit. When it asks me if I want to create a new directory, I respond yes, but get the following:

ERROR: Cannot make directory "/usr/local/Adobe/Acrobat7.0".

What do I need to do?

---

### Post by starcraft.man on 2007-05-09
> **docmeister53 said:**
> I am new to Ubuntu and am trying to install Adobe Reader using the install program in Gedit. When it asks me if I want to create a new directory, I respond yes, but get the following:

ERROR: Cannot make directory "/usr/local/Adobe/Acrobat7.0".

What do I need to do?

EDIT: Forgot to add [LINK FOR REPOS]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to adding extra repos to Feisty Fawn, I forgot that it wasn't in multiverse... I been using modified repos too long.

Ummmm, gedit is not an installer of anything... its only a text editor. It's functions don't extend beyond basic word input.

To install acrobat, please open the Terminal (Applications > Accessories > Terminal) and type this in, then hit enter:
```

sudo aptitude install acroread mozilla-acroread acroread-plugins
```

That is all ya need to do, then wait for it to finish, have a nice day :)

---

### Post by vicarious on 2007-05-10
acroread isn't in any of the standard repositories for Feisty.

---

### Post by loso on 2007-05-11
I'm having the same problem :(

---

### Post by vicarious on 2007-05-11
The easiest way is to [install automatix2](http://www.getautomatix.com/wiki/index.php?title=Installation) by downloading and double-clicking on the deb. Then start automatix2 and install acroread (it's in the office category).

I would prefer to not have to use 3rd party tools. Adobe's reader needs to be included in the multiverse, no other PDF readers allow you to fill in forms.

---

### Post by starcraft.man on 2007-05-11
Sorry about that, I forgot to point to how to add the extra repos for the new people. If you are using an older version and not feisty, add the repos for your respective version from Ubuntu guide :) (version links are at the top right before the index). I forget which of the extra repos its in, should remember for future.

The terminal code I supplied most certainly does work Vicarious, please don't send poeple to automatix2. From everything I have heard, it has caused countless problems when people upgraded, and even the odd time lead to instability in their daily use.

So visit my link I edited in for the missing repo, that should be it. Have a nice time with Ubuntu :)

---

### Post by vicarious on 2007-05-12
> **starcraft.man said:**
> The terminal code I supplied most certainly does work Vicarious
It only works if you have the Medibuntu repository enabled.

> **starcraft.man said:**
> please don't send poeple to automatix2. From everything I have heard, it has caused countless problems when people upgraded, and even the odd time lead to instability in their daily use.
Automatix caused problems when upgrading from Dapper to Edgy as did other software obtained from 3rd party repos. Recent upgrades (from Edgy->Feisty) appear to remove all unsupported software before the upgrade so this doesn't appear to be as much of an issue as it was before. I just told him to use Automatix because it was easier than the manual method. 

In fact, the method you describe is not any better. Automatix uses the same repositories that you recommend manually adding (in this case, this is the Medibuntu repository). 

Automatix is probably less risky since it doesn't (appear to) pull in updates to other software you have from these 3rd party repositories; it only pulls in the packages you specify. (Someone correct me here if I am wrong.) 

> **starcraft.man said:**
> So visit my link I edited in for the missing repo, that should be it. Have a nice time with Ubuntu :)
You described how to add a new repository but not what repository you need to add in order to get acroread. You need to add the Medibuntu repository.


I would prefer to not have to deal with any 3rd part repositories at all. It appears, however, that acroread was removed from the Ubuntu multiverse because of patent issues so we don't really have a choice on the matter.

Here is the actual way I installed acroread for those who are interested.

1. From a terminal, add the Medibuntu key to your public keyring (for security purposes, we are going to trust the Medibuntu guys):
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add -
```

2. Edit **/etc/apt/sources.list ** (with sudo privileges) and add this to the bottom:
```
# Medibuntu repository (for Adobe PDF Reader)
deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

3. From a terminal, update and install acroread (and the firefox plugin if you need it):
```
sudo apt-get update && sudo apt-get install acroread mozilla-acroread acroread-plugins
```

4. Edit **/etc/apt/sources.list ** (with sudo privileges) and comment out the repository you just added:
```
# Medibuntu repository (for Adobe PDF Reader)
**#**deb http://medibuntu.sos-sts.com/repo/ feisty free non-free
```

5. From a terminal, update the repositories again to remove the Medibuntu updates:
```
sudo apt-get update
```

Steps 4 and 5 are optional. The benefit to steps 4/5 is that you won't get updates from the Medibuntu repository you don't want. The drawback to steps 4/5 is that acroread will not automatically be updated if there is a new version or a patch, etc. If anyone knows a better way to specify which packages you want to get from which repositories, let me know.

---

### Post by zeeHesh on 2007-07-08
I was also having trouble installing acroreader, but this worked like a charm.  Thanks!

---

