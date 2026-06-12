---
title: "The Black Hole of Package Management"
date: 2021-11-30
forum: Installation &amp; Upgrades
---

### Post by Shibblet on 2021-11-30
I hope this thread belongs in Installation & Upgrades, because it is a question about software installation through the Package Manager.

When you go to uninstall software through the Software Center (Kubuntu Discover)...  Does the Software Center (or APT) actually remove the entire installation?
What I mean is things like dependencies that you only need for this one program, add-ons, extras, and the like?

For example:  If I install Firefox, and I add some extensions over it's usage period... if I click on "Remove" on Firefox in the Software Center, does it remove everything I have installed, including dependencies that I only need for Firefox?

I also would like to ask the same question for Snaps.

---

### Post by Holger_Gehrke on 2021-12-01
Of course not. Unless you do the removal with 'purge' or with 'remove' and the option '--purge' it will leave the configuration files for the package on your system. This is so that manual changes to the system wide configuration of programs don't get lost if you remove and reinstall a program for whatever reasons. It will never remove your personal configuration files.

To stay with your example: extensions to Firefox can be installed system wide or per user and the latter is the normal way and these are then seen as part of your personal configuration. So if you remove and reinstall a program you'll keep your configuration. Which is great if you reinstalled because the program file or some part of the system wide configuration broke or to free up space temporarily (don't laugh, on old systems with small drives this was a thing ... ). But if your own configuration was the the problem, than removing and reinstalling will do exactly nothing.

Dependencies are a bit more tricky. There's a database of installed packages and in that there's a field which marks a package as either installed manually or automatically (as a dependency of other packages) and a count of how many packages depend on a given package. If you uninstall a package that depends on another package the usage count for the depended on package goes down by one. Packages that are marked as automatically installed and whose usage count is zero will be removed if you run 'apt autoremove'.

What I said about personal configuration files also goes for snaps. Dependency management for snaps is different, because snaps have few if any dependencies but the ones they have are normally really big things (like for example an almost complete Gnome or KDE; snap dependencies have to be installed as snaps, so you end up having two or more instances of these - more because snap likes to keep old versions around in case you want to roll back to an earlier release).

Holger

---

### Post by Shibblet on 2021-12-01
> **Holger_Gehrke said:**
> Of course not. Unless you do the removal with 'purge' or with 'remove' and the option '--purge' it will leave the configuration files for the package on your system. This is so that manual changes to the system wide configuration of programs don't get lost if you remove and reinstall a program for whatever reasons. It will never remove your personal configuration files.
Thanks for the info on how to get rid of the configuration files.

> **Holger_Gehrke said:**
> To stay with your example: extensions to Firefox can be installed system wide or per user and the latter is the normal way and these are then seen as part of your personal configuration. So if you remove and reinstall a program you'll keep your configuration. Which is great if you reinstalled because the program file or some part of the system wide configuration broke or to free up space temporarily (don't laugh, on old systems with small drives this was a thing ... ). But if your own configuration was the the problem, than removing and reinstalling will do exactly nothing.
This is interesting, as sometimes "removing the program, and re-installing, can help to fix problems."

> **Holger_Gehrke said:**
> Dependencies are a bit more tricky. There's a database of installed packages and in that there's a field which marks a package as either installed manually or automatically (as a dependency of other packages) and a count of how many packages depend on a given package. If you uninstall a package that depends on another package the usage count for the depended on package goes down by one. Packages that are marked as automatically installed and whose usage count is zero will be removed if you run 'apt autoremove'.
Again, this is very interesting.  Can a dependency be marked as "manually installed" if it's installed along with a package from the Software Center?  Or does this only happen when a .DEB or other package is installed Manually?

> **Holger_Gehrke said:**
> What I said about personal configuration files also goes for snaps. Dependency management for snaps is different, because snaps have few if any dependencies but the ones they have are normally really big things (like for example an almost complete Gnome or KDE; snap dependencies have to be installed as snaps, so you end up having two or more instances of these - more because snap likes to keep old versions around in case you want to roll back to an earlier release).
Again, this is interesting...  I knew that Snaps had all of their dependencies "baked-into" the Snap file itself.  But I did not know it kept previous versions around as a backup.

---

### Post by ActionParsnip on 2021-12-01
The configuration will be stored in ~/.mozilla so that each user can have it's own configuration. If you don't use Thunderbird for emails then simply delete the folder and if you ever install the browser again then you will get vanilla settings.

---

### Post by Holger_Gehrke on 2021-12-01
> **Shibblet said:**
> Can a dependency be marked as "manually installed" if it's installed along with a package from the Software Center?
Yes and no ... If you install a package and it installs some other package as a dependency, that package will be marked as automatically installed. But if a package was installed during installation of the OS it normally is marked as manually installed even if it's installed to satisfy some dependency. It's done this way because some big programs are installed by having one almost empty package (usually just containing a readme file and a changelog) which depends on all the other packages that make up the program. There are packages that install a complete desktop environment this way. Imagine removing a minor part of the desktop that you don't use. This breaks the dependencies of the (almost empty) *-desktop package, so the desktop package gets uninstalled. But since the whole desktop was installed as dependencies of this package the next autoremove would remove the whole desktop ... 

And of course you have the option of marking a package as manually or automatically installed yourself with 'apt-mark'.

Holger

---

### Post by Holger_Gehrke on 2021-12-01
@ActionParsnip: There's an easier way to get a new profile for Firefox: just call 'firefox --ProfileManager' and you can create a new profile. You can then either start firefox with this profile from the profile manager or set this new profile as the default or exit the profile manager and call Firefox with 'firefox -P profile_name'. This way you can have multiple setups for different purposes with separate add-ons for one user.

Holger

---

