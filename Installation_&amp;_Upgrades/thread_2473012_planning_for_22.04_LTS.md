---
title: "planning for 22.04 LTS"
date: 2022-03-20
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2022-03-20
i am aiming to upgrade to 22.04 after the Xubuntu flavor comes out.  i am currently running Xubuntu 18.04 LTS and have skipped 20.04 LTS.  i have installed many packages on 18.04 and want to install as many of these on 22.04 as i can.

the big problem i had with my upgrade from 16.04 to 18.04 was that many package names changed.  for 18.04 to 22.04.  i want to plan this out better.  i am looking for a map of these package name changes so that i can make a script to install all the packages i need to make the new system be like the previous one.  maybe 18.04 to 22.04 is too big of a jump for one map.  two maps, one for 18.04 to 20.04 and one for 20.04 to 22.04 can be used.

i do not have a separate list of what i have added.  i only have a list of what i have now which i get from doing:
```

dpkg -l|awk '{if($1=="ii"){print $2,$4,$3;}}'

```

does anyone know of any such maps and where to get them?

---

### Post by guiverc on 2022-03-20
If all (*or just most*) your packages are found in Ubuntu repositories, why not "*upgrade via re-install*"...

eg. my old & rarely used `lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)` had Lubuntu/Xubuntu 18.04 LTS installed (*multiple desktops on same install, it may have had more too; I forget*) & I didn't want to run `do-release-upgrade` as that takes ages (*and it was unsupported for Lubuntu as 18.04 was the EOL for LXDE*) so I used that box as a QA-test for a Xubuntu 20.04 install.

I booted the RC media of Xubuntu 20.04.? LTS (*i forget which*), add the package required for my use of encrypted home partition (*no longer a default*), start the installer & select my existing partition(s) ensuring no format is tagged, then let it install.  After install I boot & check install..

Login with Xubuntu & it's 20.04 with everything looking as it should; my data survived, apps I expected are there (inc. *non-standard packages from Ubuntu repositories*)
Logout, login with Lubuntu 20.04 & it's now a LXQt desktop, everything here looked ~new as many LXDE settings aren't used on LXQt (*some remained as LXDE/LXQt are WM agnostic and Lubuntu still uses openbox*)

All my additional packages (*not default with Xubuntu - such as the `lubuntu-desktop`*) were re-installed so I passed the QA-test on iso.qa.ubuntu.com.   Sure I had to re-install my additional fonts, icons, themes etc - but that's a consequence of my storing them in /usr/share/ or a system directory which gets wiped... I don't want those saved with my user data during backups which is why they're not in $HOME where they've had survived this install; but adding them takes seconds as `nfs-common` got re-installed :) & I have a script to set that up.

I keep installs of all *supported* releases of Lubuntu for support purposes; when [21.04 reached EOL]("https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/") recently I just "*upgraded via re-install*" ([Lubuntu call it *Install with existing partition*]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743")) that system and it became a *jammy* or 22.04 one, with all my music, additional apps (*I don't use a default music player so it's a package I check gets re-installed automatically, my music continuing to play confirms user files survived*). Whatever release reaches EOL becomes the next *development* one (*my 18.04 install on this box maybe  became 21.10, I forget*)

---

### Post by tea for one on 2022-03-21
> **Skaperen said:**
> i do not have a separate list of what i have added

The following useful and effective command was created and supplied by [COLOR="#0000FF"]MAFoElffen[/COLOR] in another thread.
It is designed to list [COLOR="#0000FF"]added[/COLOR] packages for Ubuntu.
I do not know if it works in Xubuntu but worth a shot.
```
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u) >> ~/manually_installed.txt
```

---

### Post by Skaperen on 2022-03-21
every package i have is, with one exception i have logged, from Ubuntu or PyPi, the latter of which has one single repository not specific to Ubuntu releases (i have already made its install script).  i will be doing (and always do) a "fresh install" onto an empty system, that has been partitioned.  then i install additional packages followed by my added stuff such as several users and lots of files for many of them.  after that i run  another upgrade.  i do a reboot between each step.

FYI, i even used the "fresh install" method ages ago when i administered IBM mainframes running VM/CMS.

---

### Post by MAFoElffen on 2022-03-22
As you can see, I am the person who created the query that Tea For One posted...

I have since modified that to add it to the UbuntuForums 'system-info' script (In my signature line, and links posted in Sticky(s) around the Forum). In diagnostics, it is handy to see what the user has installed on their own, to see if something conflicts with what they are having problems with.

If, in current version of the 'system-info' script, you go to line #966, where it removes the temporary file storing $user_installed (that temporary file in /tmp/), and instead of removing it, rename/move it to where you want it saved... Then you will have a saved list of that in a file....
```

# change this:
rm -f $user_installed
# to something like this:
mv $user_installed $HOME/user_installed.txt

```
What that query does, is that it creates a list of installed packages that are marked as manually installed. Then it creates a list of default installed packages... Then uses compare to reconcile what is marked as manually installed, but not in what was originally installed as default... Why do I do that? Because if you reinstall something, it will remark that package as manually installed.

I use this list (previously ran during my maintenances) for migrations and for disaster recovery. I also use these in post-install scripts, to spin up "test machines". I just write a short BASH script to read the list from file, or paste the package names directly into the script to create an array... Then read the members of the array in a 'for' loop to install each. I do it with error code catching, in case a package name changed between or other problems. That makes a migration very quick and easy. With local repo's and access to the data and config files that were backed up, I've got that process down to about 20 minutes, beyond the fresh install.

There were 'some' package name changes between 18.04, 20.04, and 22.04. (That was minor) And some that are no longer in the Repo's. (That is a sore spot with me and will not mention more on that, unless something you have now or want, cannot be found.) There are even some that switched the repo they were in, to another repo... Such as from Universe to Main. I know this from updating my own Ama-Gi Project LiveCD, and trying to prepare it for 22.04. Having that list will help you determine that, to be able to plan for those changes.

EDIT:
If you were doing a do-release-upgrade... Phase One of that script, does  a package name reconciliation (between the source/installed release and the target release) that would tell you want has changed or  what is no-longer available. Those results of that can be found in the  upgrade release logs.

---

