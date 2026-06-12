---
title: "Ubuntu 10.04 to 12.04 Upgrade Fail"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by leescotland on 2012-12-30
Set my parents up with Ubuntu a year or so ago and all has been going well until they attempted to upgrade to 12.04.

I believe they left the computer and it powered off during the upgrade and will now not do any installs or upgrades.

When opening Synaptic Package Manager it says there is 4 broken packages.

These are
```
[B]libc-dev-bin
libc6-dev[/B]
libnih1
python-louis
```I have tried to "Fix Broken Packages" but i get this error.

```
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies

```Does anyone have any suggestions ?

Thanks
Lee

---

### Post by ibjsb4 on 2012-12-30
See if an update will do any good.

```
sudo apt-get update
```

Could also try a dist-upgrade (#3)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by leescotland on 2012-12-30
> **ibjsb4 said:**
> See if an update will do any good.

```
sudo apt-get update
```Could also try a dist-upgrade (#3)

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

Tried apt-get update and it comes back and says DONE but made no difference that I could see.

So i tried a distributuion upgrade and received 
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

Some other commands I read and tried,that may help have shown that liblouis0 is missing and will not install.

---

### Post by gnush on 2012-12-30
I would recommend making a fresh install instead of actually updating the distribution - it's much simpler, assuming you can back-up any files you may want to save.

> **leescotland said:**
> 
```

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you  root?
```Some other commands I read and tried,that may help have  shown that liblouis0 is missing and will not install.

It complains about permission. Either use *sudo* to run the command or elevate your privileges to root.

---

### Post by darkod on 2012-12-30
I think you need to boot into recovery mode first, not the normal mode. In the grub2 boot menu select the recovery mode entry (if the menu doesn't show by default hold Shift while booting).

That will show you a recovery menu. Select Network to activate internet, then in the same menu Drop to root shell.

That will open command prompt as root. To try to fix any broken packages and finish configuring pending packages that got interrupted, try this:
```
dpkg --configure -a
apt-get install -f
```

Note that in this root shell you don't need to use sudo in front of the command because you already are as root.

See if that helped. If it still gives you error messages, you might need to delete the file that it reports as problematic, but be careful with it, depends what that file is.

---

### Post by howefield on 2012-12-30
There are so many differences between 10.04 and 12.04 I'd recommend a clean install after backing up everything that needs to be kept.

A reinstall usually sounds a bit like using a sledgehammer to crack what should be a fairly small nut, but in terms of time it is sometimes the most expeditious route.

---

### Post by leescotland on 2012-12-30
Well been sitting here for 4 hours playing about with everything I can possibley think of and searching for every suggestion I can find on what to do with it.]

I am sad to say that I am in agreement that a clean install may be the only way to go.     Could not help but hope someone might have that magic suggestion.

---

### Post by BlinkinCat on 2012-12-30
> **leescotland said:**
> Well been sitting here for 4 hours playing about with everything I can possibley think of and searching for every suggestion I can find on what to do with it.]

I am sad to say that I am in agreement that a clean install may be the only way to go.     Could not help but hope someone might have that magic suggestion.

To me there is something "magical" about a clean installation - ;)

---

### Post by darkod on 2012-12-30
> **leescotland said:**
> Well been sitting here for 4 hours playing about with everything I can possibley think of and searching for every suggestion I can find on what to do with it.]

I am sad to say that I am in agreement that a clean install may be the only way to go.     Could not help but hope someone might have that magic suggestion.

Did you try the suggestion from my post? If you are only reading the emails without visiting the forum don't forget that you receive only the first reply. The other replies are on the forum until you visit it.

If those commands didn't help, I am all for a clean install. I never do upgrades personally, only clean installs.

---

