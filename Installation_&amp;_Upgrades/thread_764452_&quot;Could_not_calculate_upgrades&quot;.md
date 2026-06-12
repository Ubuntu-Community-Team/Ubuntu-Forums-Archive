---
title: "&quot;Could not calculate upgrades&quot;"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by tparker on 2008-04-23
I am trying to move from Dapper (AMD64) to Hardy and keep getting this same error message :
---------------
Could not calculate the upgrade

A unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bugreport.
---------------

The upgrade directions did say at the top to make sure that "dapper-updates" software channel is enabled, but it doesn't say what that is or how to do it. If that is the problem can someone please give me instructions? Or if something else is the trouble? Any help is appreciated, thanks.

I am following the official directions from the help forum for the upgrade. I started by going into Synaptic and making sure that all repositories that didn't say "officially supported" were unchecked, then I did Sys>Admin>updatemngr and made sure all updates were done. Then did alt-f2, entered gksu "update-manager -d" and followed the directions and buttons from there to re-check for updates.

It showed the new version available and started the process but during the "Setting new software channels" section I get the above error message. I have re-tried multiple times and have no clue how to continue from here. I do not know enough about Linux/Ubuntu for the error message to mean anything to me other that that something is wrong. 

I did try many forum searches and couldn't find anything related to this, I'm not sure if that is do to the forum change or my poor search skills or some of each. :)

Thanks again for any help.

---

### Post by Pumalite on 2008-04-23
Did you remove all third parties from your sources.list? Or, you might have to wait until tomorrow.

---

### Post by tparker on 2008-04-23
> **Pumalite said:**
> Did you remove all third parties from your sources.list? Or, you might have to wait until tomorrow.

I had thought unchecking them in Synaptic would do the same thing, but just to be sure I checked sources.list and it looks to be that everything that is not official is commented out. 

But I don't wanna wait! <pout> :) Really I'm just trying it tonight because I backed everything up just in case and that took about three hours. Now I'm afraid to use the computer for anything because I don't want to sit through that back-up time again to catch whatever i would change without knowing it.

---

### Post by tparker on 2008-04-24
I checked /var/log/dist-upgrade and I'm wondering if the problem is held packages. It is showing a lot of broken dependencies and held files.

The end of /var/log/dist-upgrade/main.log:

2008-04-24 01:19:21,570 DEBUG demoted: 'binfmt-support console-common console-data doc-debian evms evms-ncurses festlex-cmu festlex-poslex festvox-kallpc16k gcj-4.1-base gij-4.1 gnome-cups-manager gok gtkhtml3.8 libcompfaceg1 libdvdread3 libevms-2.5 libgcj7-jar libgda2-3 libgda2-common libglib1.2 libgnomecupsui1.0-1c2a libgnucrypto-java libgtk1.2 libgtk1.2-common libjaxp1.2-java liblzo1 libnetcdf3 libpq4 menu-xdg pmount python-eunuchs python-gadfly python-htmltmpl python-kjbuckets python-netcdf python-pgsql python-soappy python-sqlite python-stats python-syck reportbug ttf-baekmuk vnc-common xmms xvncviewer'
2008-04-24 01:20:04,829 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'

I have no clue if that is supposed to be useful information about the problem or not and can only guess at the 'held packages' part, but don't know why they would be held or how to keep them from being held so the upgrade can continue, if that is even the problem.

---

### Post by tparker on 2008-04-24
I tried again now that Hardy is officially released and I still get stopped at the same point with the same error.

There are the three causes listed in the error message:

* Upgrading to a pre-release version of Ubuntu (that's no longer the case)
* Running the current pre-release version of Ubuntu (nope, I'm still in Dapper)
* Unofficial software packages not provided by Ubuntu (I checked the repository list in Synaptic and gedited my sources.list to be sure nothing that didn't look official was available)

My /var/log is still showing lots of broken dependencies and held packages, does anyone have any idea how I go about fixing these so that the upgrade can continue?

---

### Post by tparker on 2008-04-24
Still the same error at the same point.

I have tried:
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
(nothing happened doing this, nothing downloaded, no changes made)

also tried:
sudo dpkg --configure -a
and it found no errors, did nothing, when re-tried upgrade afterward still got same error at same point.

I have been searching ubuntu forums and google and I find this same error message several places but can't find anything telling me how to fix it. Anyone fixed this before that can clue me in or have any ideas I can try?

---

### Post by Mr_Congeniality on 2008-04-24
Having the same issue here.

---

### Post by jetpeach on 2008-04-24
i have the same problem, i looked at /var/log/dist-upgrade/main.log and a complaint,
"The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
" and then it says ERROR failed...because an essential package would have to be removed.

do you guys have something similar in your main.log files?

EDIT: well i removed nvidia-glx-new and now i just have a new error in main.log - now it complains, after marking kubuntu-desktop for upgrade, that ubuntu-desktop is marked for removal but is in the removal blacklist... why is it trying to remove ubuntu-desktop?...

EDIT2: well, i removed ubuntu-desktop manually in aptitude and now it was able to calculate the upgrade! i'm giving it a go, and after it installs kubuntu-desktop i'll go back and add nvidia,ubuntu-desktop, and then third party repositories as necessary.

---

### Post by Zymous on 2008-04-24
> **jetpeach said:**
> i have the same problem, i looked at /var/log/dist-upgrade/main.log and a complaint,
"The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
" and then it says ERROR failed...because an essential package would have to be removed.

do you guys have something similar in your main.log files?

EDIT: well i removed nvidia-glx-new and now i just have a new error in main.log - now it complains, after marking kubuntu-desktop for upgrade, that ubuntu-desktop is marked for removal but is in the removal blacklist... why is it trying to remove ubuntu-desktop?...

EDIT2: well, i removed ubuntu-desktop manually in aptitude and now it was able to calculate the upgrade! i'm giving it a go, and after it installs kubuntu-desktop i'll go back and add nvidia,ubuntu-desktop, and then third party repositories as necessary.

I had a similar problem with Ubuntu except that my error message was "The package 'kubuntu-desktop' is marked for removal but it's in the removal blacklist". I'd installed the kubuntu-desktop a long time ago. Removing it allowed the installation to proceed.

-- 
Zym

---

### Post by parsim on 2008-04-25
> **jetpeach said:**
> i looked at /var/log/dist-upgrade/main.log and a complaint,
"The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
" and then it says ERROR failed...because an essential package would have to be removed.

Exact same thing here. Guess I'll postpone upgrading until I have time to frig around with it.

---

### Post by tparker on 2008-04-25
[QUOTE=jetpeach;4784012]
"The package 'nvidia-glx-new' is marked for removal but it's in the removal blacklist
" and then it says ERROR failed...because an essential package would have to be removed.

do you guys have something similar in your main.log files?


I do not, I checked main.log again and mine doesn't have trouble with removal blacklist stuff, it's all broken dependencies and held packages that seem to be stopping my upgrade. I still haven't been able to find any information on how to either fix the dependencies and/or un'hold' the files to get past this part and on to whatever implodes the upgrade next. :) 

I have downloaded the .iso for a fresh install in case it comes to that but am holding off for now hoping I can get the upgrade to work. My current install was set up with help from someone who knows Linux much better than I and my /home is over on another computer (NFS). I'm unsure how to set things up in a new install to be sure I don't blow away by current /home but can still access it after the install is done.

Anyone have a clue how to fix the broken dependencies or clear up the held packages?

---

### Post by ribes on 2008-04-25
I found the perfect thread. I too am trying to upgrade from Dapper.

I got the "Could not calculate" message. Removed the "third party" source and purged some packages from universe and multiverse that were being "held back".

So I got past the "could not calculate", but THEN it went into a kind of infinite loop that grew the apt.log something humongous and worked the hard drive. After about a day, I killed the "hardy" python program.

I think my next step will be to remove the gui. This is kind of a server system (dhcp, dns, asterisk, routing) but I'm not sure how to begin. I sure don't want to wipe it clean and start over.

Any ideas?

---

### Post by parsim on 2008-04-25
> **parsim said:**
> Exact same thing here. Guess I'll postpone upgrading until I have time to frig around with it.

After removing the offending package (nvidia-glx-new), the upgrade completed with out a hitch for me.

---

### Post by parsim on 2008-04-26
> **parsim said:**
> After removing the offending package (nvidia-glx-new), the upgrade completed with out a hitch for me.

Oh, except when I first booted into X, it said it couldn't detect my vid card and dumped me into low-graphics mode. I had to disable and re-enable the "restricted" NVIDIA driver in System -> Administration -> Hardware Drivers.

---

### Post by igave on 2010-05-04
I had the same error.
I removed ubuntu-desktop
sudo apt-get remove  ubuntu-desktop
That worked for me

---

### Post by igave on 2010-05-04
:d> **igave said:**
> i had the same error.
I removed ubuntu-desktop
sudo apt-get remove  ubuntu-desktop
that worked for me

---

### Post by haidoura on 2010-05-07
look into the upgrade logs for any broken depends packages and install them
```
cat /var/log/dist-upgrade/apt.log | grep broken
```

---

### Post by radiobert on 2010-10-11
You can try using aptitude to find broken packages: $ aptitude

---

### Post by deceaseddolphin on 2011-02-07
> **igave said:**
> I had the same error.
I removed ubuntu-desktop
sudo apt-get remove  ubuntu-desktop
That worked for me
Great, your solution worked for me as well!

Cheers.

---

### Post by shanzou on 2011-05-01
had same problem,removed ewery lib whit word "nvidia" in synaptic.now upgrading

---

### Post by MickAgain on 2011-12-24
> **shanzou said:**
> I had the same problem, removed every lib with the word "nvidia" in synaptic. Now it's upgrading

Worked for me as well.

---

### Post by oldos2er on 2011-12-24
Closed, necromancy.

---

