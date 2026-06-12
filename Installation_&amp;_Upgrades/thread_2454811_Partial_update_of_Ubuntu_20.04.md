---
title: "Partial update of Ubuntu 20.04"
date: 2020-12-06
forum: Installation &amp; Upgrades
---

### Post by 1009ebwong on 2020-12-06
[FONT=Verdana]Hi![/FONT]
[FONT=Verdana]I was attempted to upgrade my Ubuntu Linux 18.04 to 20.04. I did ```
sudo do-release-upgrade
``` at first. Then after the system checking for the updates, there was an instruction to press "Enter" button in order for the update to proceed. I am not really confident with the command line upgrade so didn't proceed with "Enter". I aborted it and go with the GUI update in "Software &amp; Update". Before proceeding the update, I did ```
sudo apt update
``` and ```
sudo apt upgrade
``` (I guess some of the updates for Ubuntu 20.04 were running during this phase). After the commands are done, I carried on with the GUI update. There was an error popping out when the "installation of packages" almost completed. Saying "The upgrade has aborted. Your system could be in an unusable state. A recovery will run now (dpkg --configure -a)." According to the schedule shown on screen, the next phase should be cleaning up and then restarting. But nothing seemed to be running after that. Then I restarted Ubuntu manually. I saw some different icons appeared in my screen and a number of new icons on the menu list. I guess those are from version 20.04. However, there was still chunks of the icons from 18.04 left over in the menu list. For example, I have duplicates of "Files" and "Software &amp; Updates" in the menu list, both the old version and latest version. I am worrying that the update was not completed and not sure what I should be doing next.[/FONT]

[FONT=Verdana]The summarized steps I was conducting for the updates:[/FONT]
[FONT=Verdana]sudo do-release-upgrade (without starting the update run)[/FONT]
[FONT=Verdana]sudo apt update[/FONT]
[FONT=Verdana]sudo apt upgrade[/FONT]
[FONT=Verdana](GUI) Software & Updates -- proceed with Ubuntu 20.04 update and it stopped at "Installing the upgrades"[/FONT]
[FONT=Verdana]Restart Ubuntu manually[/FONT]

[FONT=Verdana]I am not sure what I should be proceeding next. Should I do apt update & apt upgrade? or dpkg --configure -a? or apt dist-upgrade?[/FONT]

---

### Post by Impavidus on 2020-12-07
Have a look at your software sources in /etc/apt/sources.list. Skip the lines starting with #. All lines should refer to focal.

Then run```
sudo apt update
sudo apt full-upgrade
```That will make sure you've upgraded all software to the latest versions for 20.04.

There may still be leftovers from 18.04. The ones that were automatically installed can be removed with```
sudo apt autoremove --purge
```

That still leaves packages marked as manually installed (which included packages installed during the initial install of the system) that were not upgraded for Ubuntu 20.04, but replaced with a package with a different name. They are no longer available for download and install, but may still be installed. You can remove them, if their replacements have been properly installed. I think the simplest way is using the synaptic package manager. Look for status &#8594; installed (obsolete or manually installed). Read descriptions and check the dependencies synaptic wants to remove. Some packages may not be obsolete.

Also look for transitional dummy packages. Those are used when a package changes name. A package with the old name is still around, but only to make the upgrade run smoothly and pull in the package with the new name. Search for the description "dummy" (but note that not all packages with that word in their description are dummy packages, so read the full description).

---

