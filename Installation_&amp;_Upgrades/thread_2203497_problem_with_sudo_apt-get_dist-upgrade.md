---
title: "problem with sudo apt-get dist-upgrade"
date: 2014-02-03
forum: Installation &amp; Upgrades
---

### Post by mark_ricketts on 2014-02-03
etched 1,217 kB in 2min 0s (10.1 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.

I get the above error message after trying "sudo apt-get update && sudo apt-get dist-upgrade".  I tried "dpkg --configure -a" to no avail and also looked for any ppa with the "steampowered" tag associated.  Can anyone suggest someplace else to try.

---

### Post by Bashing-om on 2014-02-03
mark_ricketts; Hi !

Let's say that a control file has become corrupted:
Remove and regenerate the index files:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get update
sudo apt-get upgrade

```

Please then to advise of the status.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by mark_ricketts on 2014-02-04
Thanks Bashing-om your suggestion solved my major road block and allowed me to move on from where I was stuck.  If I might ask...can you explain what was going on with your second command suggestion...this line.

sudo mkdir -pv /var/lib/apt/lists/partial

why did this work?  What is it telling the computer to do.  Is it saying to re-create the missing parts of the directory above the /var/lib/apt/lists/partial?
If yes, wow...what a powerful command.  I've got to aquaint myself more with the Linux command line.  Impressive.

---

### Post by Bashing-om on 2014-02-04
mark_ricketts; Hey,

Pleased things are working out for ya.

Breakdown:
sudo rm -fr /var/lib/apt/lists : ->storage area for state information for each package resource specified in sources.list
Rm removed these control files.

sudo mkdir -pv /var/lib/apt/lists/partial : ->storage area for state information in transit.
We removed this directory with the above remove command, and it is required. Maybe it will get recreated, just to make sure it is available, make dir and create it ourselves .

sudo apt-get update : syncs your system data base with that of the mirror's more recent data base; recreating the control files required - that we previously removed. These should now be consistent to all packages installed on your system.

sudo apt-get upgrade : updates all your installed packages to what is current on the mirror.

As you can imagine, there is a whole bunch going on in the background. This is the most powerful system in existence today. But, like any tool, one has to learn how to use it.

This is your friendly neighbor hood ubuntu forum. We do ubuntu, any time you have a question or something that you do not understand; we are but a keyboard away.

As this little situation is in hand:
Please mark this thread solved; aids others seeking a similar solution and as well, helps keep the forum tidy.


[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

