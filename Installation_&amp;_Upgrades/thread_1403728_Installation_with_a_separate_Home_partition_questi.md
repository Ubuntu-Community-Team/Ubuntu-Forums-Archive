---
title: "Installation with a separate /Home partition question"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by Paulgirardin on 2010-02-10
Doing a new intstallation of the next distro and retaining the existing /Home in its own partition,is it necessary to download all the applications used in the previous distro

(I use: )
```
dpkg --set-selections < installed-software
```

or is this unnecessary and is covered by using the old /Home contents?

---

### Post by darkod on 2010-02-10
I'm quite fresh in ubuntu but as far as I know having separate /home does NOT keep all your packages. It just keeps some settings on top of your personal files.

I think you still need to do the save packages commands. More details for them:
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by Paulgirardin on 2010-02-10
That's how I understand it too.
Thanks for the comment

---

### Post by dabl on 2010-02-10
> **Paulgirardin said:**
> 

is it necessary to download all the applications used in the previous distro



No.

Before reusing that directory, you might want to use your file manager and turn on "view hidden" and review the hidden folders, which contain "settings".  A lot of the names are self-explanatory.  For any hidden folder that is designated for a package that you are NOT planning to install again, you might want to ```
mv .xyz .xyz_old
``` so that it doesn't inadvertently interfere with the setup of your new system.  Same goes for any prior settings that you are not entirely pleased with, such as .mozilla, etc., if you'd rather make a clean start with the new version.

---

### Post by Paulgirardin on 2010-02-10
Prior to the last install I backed up the contents of /Home and replaced them into /Home after the install.
So if I understand Dabl correctly,I do not need to reinstall selected apps if they are the same ones from the previous install.

---

### Post by darkod on 2010-02-10
> **Paulgirardin said:**
> Prior to the last install I backed up the contents of /Home and replaced them into /Home after the install.
So if I understand Dabl correctly,I do not need to reinstall selected apps if they are the same ones from the previous install.

Well, it up to dabl to explain, but I think there was a small misunderstanding between the two of you. I think he wanted to say that you might as well delete the settings of packages you DON'T want to install again after the clean install.

> 
 for a package that you are NOT planning to install again

---

### Post by ajgreeny on 2010-02-10
Sorry, but you will definitely need to install again all the new versions of the packages that you personally added to your last version of ubuntu.  Only the config files will still be in your separate /home partition, not the actual applications themselves.  Any apps in the vanilla ubuntu will, of course be installed, and barring upgrades to those default applications in the installed version, you will not need to do any more.

---

### Post by dabl on 2010-02-10
Right - aj has said it correctly.

There are no "packages" in your user's home folder, but there are a ton of configuration settings _for_ packages.  I'm recommending:

a.  For packages that you never intend to use again, you find the associated .xyz folder in your user's home folder and either delete or mv it.  For example, if you tried the Chrome browser, and decided you hated it, then there is no reason to keep its hidden file in your home folder in the new installation.

b. For packages that you do want in the new installation, but were all buggered up in your prior installation, you also want to delete or mv the hidden folder.  For example, if Firefox was all messed up with plugins that you don't want and such, then just nuke the .mozilla folder and when you install Firefox on your new system, you will have the opportunity to set it up fresh, with no carryover from the prior installation.

The bottom line -- for every package in your old system, the settings will carry over to your new system if you don't remove or rename the ".xyz" configuration folder in your user's home directory.

---

### Post by Paulgirardin on 2010-02-10
Ok that's clearer.
Thanks for the tips

---

