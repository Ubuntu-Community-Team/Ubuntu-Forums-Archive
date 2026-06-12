---
title: "Ubuntu 22.04.1 LTS Doesn't auto update?"
date: 2023-02-14
forum: Installation &amp; Upgrades
---

### Post by cybrsaylr on 2023-02-14
All previous Ubuntu versions would say, updates are available and show them. Would then click on them to have them install and update my system.

22.04 LTS does not do this.

To update and install I have to use use terminal with these codes:

Sudo apt update

Sudo apt upgrade

After using terminal with them codes, then 22.04 will update.

Why doesn't 22.04 update as easily as earlier versions?

---

### Post by ajgreeny on 2023-02-14
Open up **Software and updates** to see what settings you have there for showing updates are available.

As far as I'm aware 22.04 is no different from previous versions so you must have a setting that stops the update manager from showing they are available.

---

### Post by BBQdave on 2023-02-14
**Software Updater** handles updates for both .*deb* and *snap*. I believe it is on a schedule, maybe weekly. Update message will appear in between schedule if the update(s) are critical.

You can check your schedule by running **Software Updater** and then selecting *Settings*. *Settings* will open **Software and Updates** and show the schedule for your system's updates. The default setting is to immediately install (message to install) critical updates and most others occur weekly.

---

### Post by cybrsaylr on 2023-02-14
Here's what I have set up in Software & Updates but to update I have to use terminal.
However Software Updater always says, The software on this computer is Up To Date.

[IMG]https://i.postimg.cc/C17QxLX9/Screenshot-from-2023-02-14-10-36-24.png[/IMG]

For example last night, Software Updater said, The software on this computer is Up To Date.

Went into terminal with those 2 codes; 

Sudo apt update

Sudo apt upgrade

Terminal then said there were about 74mgs of updates to install and did that with those 2 codes in terminal to install those updates.

---

