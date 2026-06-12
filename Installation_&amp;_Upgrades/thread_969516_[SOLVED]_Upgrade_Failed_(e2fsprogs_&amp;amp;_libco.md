---
title: "[SOLVED] Upgrade Failed (e2fsprogs &amp;amp; libcomerr2), upgrade-manager now broken"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by BassKozz on 2008-11-03
I am trying to upgrade from Hardy (8.04) to Intrepid Ibex (8.10)... 
I went into System>Administration>Software Sources, and I changed Release Upgrade; Show new distribution releases from **Long Term Support Releases Only** to **Normal Releases**.
I then went into System>Administration>Update Manager and found the option to upgrade to 8.10 ("New distribution release '8.10' available") and I chose to upgrade.

After about 20minutes of downloading packages it began installing the packages, I walked away from my computer and came back to find it frozen :(
I rebooted the machine and an error reporting modual popped up and asked me if I'd like to report an error for developers to look into, I complied and tried to report the bug to launchpad but firefox crashed and I lost the report before I could file it... I do know how ever that the issue had to do with **e2fsprogs** and **libcomerr2** failing to install/upgrade because I could grab that from the URL that the error reporting modual sent to firefox.

Now when I open up the update-manager I get the following error message:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-update-manager.png[/IMG]
And when I click '**Close**' I get the next screen:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-update-manager-1.png[/IMG]
When I tried to run '**sudo apt-get install -f**' as the error message says to do I get the following results:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
  libcompress-raw-zlib-perl: Depends: perlapi-5.10.0
  libcups2: Depends: libgnutls26 (>= 2.4.0-0) but it is not installed
  libhtml-parser-perl: Depends: perlapi-5.10.0
  libperl5.10: Depends: perl-base (= 5.10.0-11.1ubuntu2) but 5.8.8-12 is installed
  libuuid-perl: Depends: perlapi-5.10.0
  perl: Depends: perl-base (= 5.10.0-11.1ubuntu2) but 5.8.8-12 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
```
When I try to '**check for updates**' by right clicking on the update managers taskbar notifier I get the following two error messages:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-synaptic.png[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-synaptic-1.png[/IMG]

What do I do now? I am lost...
Please Help,
Thanks,
-BassKozz

---

### Post by BassKozz on 2008-11-03
**_UPDATE**_
I tried to do a '**Partial Upgrade**' from this screenshot:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-update-manager.png[/IMG]
and I got the following screens in this order:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-DistributionUpgrade.png[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-update-manager-2.png[/IMG]
[IMG]http://i4.photobucket.com/albums/y105/basskozz/Ubuntu/upgrade-home-to-intrepid/Screenshot-update-manager-3.png[/IMG]

Now I really have no where to go, any idea's?

---

### Post by BassKozz on 2008-11-03
:BUMP:
I think I found out why the upgrade failed...
One of my memory sticks could possibly be bad: [HardOCP Forums Post]("http://www.hardforum.com/showthread.php?p=1033261991#post1033261991")

So now that I've got that out-of-the-way, how can I get synaptic fixed?

---

### Post by BassKozz on 2008-11-03
I think I fixed it...
I went into the Synaptic-Package-Manager and filtered all the **BROKEN** packages (there were 6 of them) and re-installed them, and I am now upgrading to 8.10 :D
I'll post an update once I've upgraded successfully.
Thanks,
-BassKozz

---

### Post by BassKozz on 2008-11-04
It's fixed, Upgrade completed successfully,
But of course now I've run into some other problems: [Problems with Intrepid]("http://ubuntuforums.org/showthread.php?p=6104435#post6104435") :(

---

