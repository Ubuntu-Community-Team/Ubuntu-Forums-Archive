---
title: "Anyone make Miro or Elisa with libffi5?"
date: 2008-06-15
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by autocrosser on 2008-06-15
I've been missing Miro since I updated libffi4 to 5--Elisa also has a 4 depend--has anyone made or patched either to work with 5?

---

### Post by ShirishAg75 on 2008-06-15
Its not just Miro and Elisa , also Postr needs libffi4 and hence missing in action as well  :(

Perhaps we just need to wait for updated build copies.

---

### Post by autocrosser on 2008-06-15
Yes--I looked at Miro's site & they are still working with 4--tried to build it myself & had a no joy :(

---

### Post by RAOF on 2008-06-15
I think that's a libboost issue, possibly version related, but I haven't really investigated yet.  If you manage to get Miro to build, feel free to post on my merge bug ;).

---

### Post by ubulette on 2008-06-16
boost needs to be merged from Debian first. the Ubuntu version, built with gcc 4.3 is not usable to build miro. This has been fixed by Debian since 1.34.1-6.

---

### Post by plun on 2008-06-17
Warning for Elisa, I haven't checked SVN for a while but earlier it
was a big mess to install from source.  All python "eggs" must be checked
if a user wants to switch to packages.

Another alternative with risks is to take Debians unstable packages.

For Google Gadgets I am using Sids packages (SSL etc) and compiles from source.

Nevertheless this bug seems to be important to solve.

---

### Post by bobpaul on 2008-09-29
[B][EDIT]: 


This entire post appears to be irrelevant. The new miro is already in the repository. I'll leave this here as historical documentation, though.

[/EDIT]
[/B]

After the recent update that installed libffi5, I did the following to allow me to still use miro. Note that I would not recommend this as it will probably leave some things acting weird. So far I haven't noticed any major problems, though...

**Installed old packages from Hardy**

I downloaded the following packages from packages.ubuntu.com:
libboost-date-time1.34.1_1.34.1-4ubuntu3_amd64.deb
libboost-python1.34.1_1.34.1-4ubuntu3_amd64.deb
libboost-thread1.34.1_1.34.1-4ubuntu3_amd64.deb
libffi4_4.2.3-2ubuntu7_amd64.deb
libgdl-1-0_0.7.11-1_amd64.deb
libgdl-1-common_0.7.11-1_all.deb
libgdl-gnome-1-0_0.7.11-1_amd64.deb
miro_1.2.7-0pcf1_amd64.deb
miro-data_1.2.7-0pcf2_all.deb
python-gnome2-extras_2.19.1-0ubuntu7_amd64.deb

You'll need to use "dpkg -i" to install them as gdebi will attempt to resolve dependencies using the repositories, which will of course make it try to pull in libffi5 again. You'll also need to uninstall the current versions of these packages or any packages that conflict using "apt-get remove".

For the libffi4 package I had to force dpkg to ignore the dependency on gcc-4.2-base (= 4.2.3-2ubuntu7). See dpkg --force-help for info.

*If you just do this, you're done but your system will have a broken package (libffi4) and will prevent you from installing any new packages without doing 'apt-get dist-upgrade', removing miro, and upgrading to libffi5 again. If you don't mind repeating the above after installing a new program, that's fine. If not, read on.*

**Unsafely and manually play with apt's status file**

DO NOT DO THIS. You will screw up and make a big mess of things. I'm very lucky that I haven't yet. I would not recommend installing updates, but you can do the following to carefully install new applications or remove existing programs without affecting your manual miro install.

The file /var/lib/dpkg/status is very similar to the "world" file if you're familiar with portage on Gentoo. It lists all the packages you've ever installed on your system, whether they are currently installed or if they were previously installed and have now been removed or purged. This file also contains a lot of other information about the packages, including dependencies, info to display via 'apt-cache', etc. White space is important, so preserve it. There should be one blank line between packages.

*First, backup the file:*
cp /var/lib/dpkg/status ~/status

*Remove Info that's causing problems*
Go through by hand and remove all info about the packages you installed in the first step (those *.debs you manually downloaded). Be sure to remove the whole "paragraph" relating to your package and leave 1 blank space. Test something like "apt-get install miro" and see if you get parse errors when done. If not, you've done well.

*Copy the info for just those packages into a diff-file:*
diff status ~/status > ~/status-diff

*Edit your status-diff file*
Open status-diff with gedit out the diff notation (remove the > from the beginnings of the lines and the lines that say things like "1,37d0".

*Install your new programs*
~/status-diff now contains the info for the pakges you installed manually only. At this point you can install new programs, but be sure to check what apt-get plans to install. Right now it does not know about those packages you installed with dpkg in the first step, so it may try to install things like libffi5 without removing libffi4 and all those other packages. THIS IS WHY I DON'T RECOMMEND ANYONE DO THIS.

*Restore the package info from the diff*
cp /var/lib/dpkg/status ~/status
cat ~/status-diff ~/status > sudo tee /var/lib/dpkg/status >/dev/null

Congratulations. Your status file now contains the new packages you installed as well as the info for those "broken" packages that were preventing you from doing anything Hopefully soon the miro package will be fixed and you can simply 'apt-get dist-upgrade' to install the new miro with proper dependencies. In the future you can simply remove the first 137 lines of /var/lib/dpkg/status and then repeat the "Restore the package info" step as you already have a good status-diff.

---

