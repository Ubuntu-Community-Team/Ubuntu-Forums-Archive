---
title: "No kppp after dist upgrade"
date: 2009-12-08
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by YosefKaro on 2009-12-08
After todays dist. upgrade, I can't use kppp.  I have to use kppp for my internet.  Even when I enter gksudo kppp to launch it, I get prompted for my password then after I enter it, nothing happens.  It was a real pain for me to set up kppp just right so I don't want to have to do it all again.  Any ideas what may have happened here?

-Yos

I just tried a re-installation...that didn't help any.

---

### Post by YosefKaro on 2009-12-08
Now I just finished a complete removal of kppp from my computer and then a re-install.  kppp just does not work at all anymore :(

-Yos

---

### Post by kansasnoob on 2009-12-08
Packages have been in a state of flux for over 24 hours pending the release of Alpha 1. Were you not warned of this being a partial upgrade? What method did you use to upgrade?

Regardless, when the packages get straightened out, you could either reinstall or you could mount and chroot Lucid as I explained here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

You would then apt-get update && apt-get dist-upgrade. But I'm not sure how soon the packages will be straightened out.

---

### Post by slakkie on 2009-12-08
> **kansasnoob said:**
> Packages have been in a state of flux for over 24 hours pending the release of Alpha 1. Were you not warned of this being a partial upgrade? What method did you use to upgrade?

Regardless, when the packages get straightened out, you could either reinstall or you could mount and chroot Lucid as I explained here:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

You would then apt-get update && apt-get dist-upgrade. But I'm not sure how soon the packages will be straightened out.

You warn about Partial upgrades, yet you advise him to perform partial upgrades.

Use apt-get upgrade or aptitude safe-upgrade instead. If you see held back packages, that are your partial upgrades. Then perform the dist-upgrade, you void your warranty when performing the partial upgrade ;) aka, read the partial upgrade thread.

On a side note, could you post logs of what is going wrong, unless we get telepathic powers we cannot know what is going wrong at your side.

---

### Post by kansasnoob on 2009-12-08
> You warn about Partial upgrades, yet you advise him to perform partial upgrades.

I'm talking about attempting to complete a failed partial update/upgrade through a chroot.

I would certainly use dist-upgrade in that particular situation! I also made it clear that it's not going to work until the packages are straightened out.

Regardless of which upgrade command you use you still get an opportunity to review what's going to be removed, installed or upgraded.

On a running desktop I actually prefer using synaptic, but that's not the situation we have here. In fact they have no internet, which should be resolved via "cp /etc/resolv.conf /mnt/etc/resolv.conf" from the Live Desktop so they can access package management.

---

### Post by Yes_It's_Me on 2009-12-08
Right now hardly any KDE apps work. I think it's because of the kdebase-runtime package. The new build isn't up yet a whole lot of other KDE stuff was pulled in in todays upgrades, which borked all KDE programs. Qt apps work fine however.

---

