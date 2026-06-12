---
title: "Lubuntu 18.04 Package Error"
date: 2020-07-20
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2020-07-20
Synaptic Package Manager starts, then shows following error message:
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_bionic_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

The OS installs and runs, with the error message.
Can browse, run Firefox Ok, applications seem to open etc.

Software Updater seems to start, then terminate without any dialogue boxes or errors.

Asrock Mobo desktop with UEFI, a few years old as it has a Windows 7 sticker on it:
 - out-of-service some years ago when it got "too difficult to use" with Windows, and the hard disk removed,
 - I acquired it, added HD and installed LinuxCNC,
 - the Debian 7 Wheezy OS used for LinuxCNC seemed Ok,
 - Ubuntu 20 LTS attempted install with error message similar to above,
 - then Lubuntu with errors.

I am reasonably Ok on the Command Line, with guidance.
Any hints on where to look ?

Keep well,
John.

---

### Post by Bashing-om on 2020-07-20
electrosteam; Hello -

MergeLists are a working tool of apt, part of the way it keeps track of which packages are in which repositories. It's the gears of a text-based database that apt relies upon. When corrupted, they can be safely deleted. Apt will recreate them during the next apt update.
Run:
```

sudo rm -fr /var/lib/apt/lists
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt update
sudo apt upgrade

```

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2020-07-20
Hi, I think this will solve your issue, please do:
```
sudo rm /var/lib/apt/lists/* -vf
```
The first command will remove the damaged list and when you run the second command it will replace it with a new list.
```
sudo apt-get update
```

---

### Post by electrosteam on 2020-07-21
Thanks guys,
applied the suggestion by Wildmanne39 inside Lubuntu 18.04.

Went well.
Synaptic Package Manager opens normally.
Software Updater opens normally and reports 434 MB download required to make current.

I will now attempt a Ubuntu installation.

Keep well,
John.

---

### Post by electrosteam on 2020-07-23
The Ubuntu install did not go well.
Each time I tried, the result was different:
 - stalls at a different step,
 - error messages different,
 - sometimes prompt for error report, but without the email dialogue entry option,
 - never got to anything that would operate.

Gave up and did a fresh install of Lubuntu.
Absolutely beautiful, not a single glich.
Got a system that Software Updater reports as up to date.

I started Linux with Lubuntu 17.10 and waited for 18.04.1 before upgrading.
Not a problem.
I now have a new laptop, but I am settled in to Lubuntu and not tempted to even try Ubuntu.

This computer is for a friend, and if he wants the "bells and whistles". I will try Ubuntu again when the 20.04.1 offered.

Keep well,
John.

---

### Post by Bashing-om on 2020-07-23
electrosteam; YaY :D


Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

