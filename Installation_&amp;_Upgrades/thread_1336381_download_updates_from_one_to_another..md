---
title: "download updates from one to another."
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by windowsfree on 2009-11-24
Is it possible to download programs and updates and install them on another machine?
The other machine does not have any internet access.

---

### Post by mac9416 on 2009-11-24
Howdy,

There are two ways of doing this. 

_**Method for all Ubuntu computers (using APT)**_

[LIST=1]
[*] Install the packages/updates on an online machine
[*] Copy /var/cache/apt/archives/ and /var/lib/apt/lists/ to a flash drive
[*] Move them to the offline computer (overwriting the existing folders)
[*] Run 'sudo apt-cache gencaches' (to update the lists of available packages)
[/LIST]

Alternatively, you can use [APTOnCD]("http://aptoncd.sourceforge.net/") to create a CD repository of the packages.
 
Now you can install any packages that you had installed on the online computer.

**Drawbacks:**
[LIST]
[*]You can only do this if the two machines are identical. (Same Ubuntu version/flavor)
[*]you can only do this if the online computer runs Ubuntu. (Not Windows)
[/LIST]

If those are not a problem, go with that method. If not, read on...

**_Method for Ubuntu/Windows computers (using [Keryx]("http://keryxproject.org"))_**


[LIST=1]
[*] Download [Keryx]("http://keryxproject.org")
[*] Create a project on the offline computer (read the [tutorial]("http://crashsystems.net/2009/01/keryx-tutorial/") for instructions)
[*] Take Keryx to your online computer and download the packages/updates
[*] Copy the files from <flash_drive>/keryx-0.92.3/projects/<project_name>/packages/ and <flash_drive>/keryx-0.92.3/projects/<project_name>/lists/ to /var/cache/apt/archives/ and /var/lib/apt/lists/ respectively
[*] Run 'sudo apt-cache gencaches' (to update the lists of available packages)
[/LIST]
 
Again, you could also use [APTOnCD]("http://aptoncd.sourceforge.net/") to make a CD repo from the debs.

Sorry for the long-winded post. Hope it helps! :)

---

### Post by windowsfree on 2009-11-25
Thanks, APT on CD is what I will use.  Thank you!

---

