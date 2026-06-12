---
title: "List of user-selected packages"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by Prendi on 2007-12-27
Hi,
is there a way to output the list of all packages that were installed on the system because the user chose them to be installed (i.e. they are not installed as a dependency?) through synaptic/adept/apt-get/whatever.

I essentially need a list similar to the Gentoo world file. I know that the question has been asked several times on this forum, but it has never been answered correctly. I know, that dpkg can output a list of all installed packages, but I want a list only of those packages that were not installed as a dependency. 

My main reason is, that whenever I tell Ubuntu to install a package, this package and all of its dependencies get installed. If I forget about these packages, their whole dependency trees will stay installed and will need to be updated. On the other hand, if I have a list of these packages, I can remove them with apt-get and then remove their dependencies with "apt-get autoremove".

For example, I installed Xubuntu on a laptop computer. I didn't like it too much, so I just used apt-get to install the package kubuntu-desktop, effectively switching to Kubuntu. Now, I'd like to remove the remains of Xubuntu, but removing the xubuntu-desktop package and the doing "apt-get autoremove" doesn't seem to be enough.

---

### Post by PmDematagoda on 2007-12-27
```
ls /var/cache/apt/archives
```
Should give you a rough list of the packages installed by the user since the packages that are installed are downloaded and stored in the archives folder.

---

### Post by icheyne on 2007-12-27
how about trying ```
sudo aptitude --show-deps xubuntu-desktop
``` and then uninstalling those packages?

---

### Post by Prendi on 2007-12-27
> **icheyne said:**
> how about trying ```
sudo aptitude --show-deps xubuntu-desktop
``` and then uninstalling those packages?

It seems, aptitude --show-deps only works as a parameter to the install and remove commands. And even there, it only shows dependencies that are not currently installed. Hence, running the command you suggested when xubuntu-desktop is already installed doesn't output anything, because all dependencies are already satisfied. Also, it wouldn't help removing all packages that xubuntu-desktop depends on, because other programs may depend on these as well (for example, AFAIK xfce needs GTK, but I shouldn't remove GTK, since Gnome needs it as well).

That's the beauty of the Gentoo approach: You essentially just tell the system that you don't need the xubuntu-desktop package anymore (by removing its entry from the world file) without actually removing it. Then, you just tell the system to do an autoclean, which will get rid of the package itself as well as of all other packages that nothing else depends on.

@PmDematagoda:
I know that I could just search the package cache, but that only gives a ROUGH overview over ALL the packages that have been installed RECENTLY. I'd like to get an EXACT list of ONLY THOSE packages that I CHOSE to install no matter how long ago (as long as the package is still installed). Anyway, thanks for the idea.

There should be an internal list of apt somewhere that contains exactly what I need, since "apt-get autoremove" should depend on something like this list.

---

### Post by icheyne on 2007-12-27
I have always found that Aptitude does everything I need as it uninstalls automatically installed dependencies - sounds similar to the world file. YMMV.

---

### Post by Prendi on 2007-12-28
> **icheyne said:**
> I have always found that Aptitude does everything I need as it uninstalls automatically installed dependencies - sounds similar to the world file. YMMV.
Yeah, and AFAIK so does apt-get. My problem is, that I'm not necessarily aware of which packages I installed manually. Lets say I install the glibc developer packages to compile my own programs. If I forget that I installed this package, it and its dependencies will never get deleted. 

But it should show up in a world file with only 20 or so other packages (ubuntu-desktop being one of them). This way, I can easily identify it as a package that I don't need any longer, I can remove it from the world file (or remove the package) and let apt-get/aptitude/whatever clean out the dependencies.

---

### Post by icheyne on 2007-12-28
I think apt-get is discussed at the [email]deity@lists.debian.org[/email] mailing list. You might find a solution there.

---

### Post by andmalc on 2007-12-30
aptitude search '~i!~E' | grep -v "i A" | cut -d " " -f 4

---

### Post by icheyne on 2008-02-06
dpkg --get-selections > pkg.list

---

