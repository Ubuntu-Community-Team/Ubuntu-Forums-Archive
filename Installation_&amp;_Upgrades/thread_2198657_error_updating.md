---
title: "error updating"
date: 2014-01-09
forum: Installation &amp; Upgrades
---

### Post by richard-smith7-gmail on 2014-01-09
I'm trying to fix an issue in my daughter's computer. She's running Ubuntu 12.04LTS and when she tries to update she gets the error:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Unable to parse package file /var/lib/apt/lists/ca.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages (1), E:The package lists or status file could not be parsed or opened.'

I have no idea what that means or what I should do next.

---

### Post by Bashing-om on 2014-01-09
richard-smith7-gmail; Hi !

Let's take an easier approach to the situation and "assume" that the control files have gotten corrupted and the package management system is in an inconsistent state.
This can do no harm, and maybe all to the good !
Try terminal codes:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo rm /var/lib/apt/lists/partial/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
update rebuilds the index files that were removed. and upgrade will update all installed packages to the latest versions that are in the software repository.

Advise us of the results.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by richard-smith7-gmail on 2014-01-11
Aw, thank you Bashing-om. It turns out she had another problem, which was that she couldn't save anything. Your suggestion fixed that too, so everything now works, she is happy and I look like a god.

I really appreciate your help.

Richard

---

### Post by Bashing-om on 2014-01-11
richard-smith7-gmail; Hey outstanding,

We will never tell.

As the situation is now under control, please mark this thread as solved (1st post -> thread tools). This aids others seeking a similar solution and helps keep the forum tidy.

[INDENT][INDENT]just keep on keep;n on
[/INDENT][/INDENT]

---

### Post by richard-smith7-gmail on 2014-01-21
Unfortunately, the error is back, or at least a similar one. I tried the same code you gave me, but it doesn't seem to work this time. This is the error:

  Could not initialize the package information

An unresolvable problem occurred while initializing the package information.


Please report this bug against the 'update-manager' package and include the following error message:


'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by Bashing-om on 2014-01-21
richard-smith7-gmail; Well !

I am kinda covered up presently, lemme get caught up and clear my faculties. 
Will see what I can come up with,

later 
[INDENT][INDENT]as in later
[/INDENT][/INDENT]

---

### Post by Andrew_P on 2014-01-22
> **Bashing-om said:**
> 
Let's take an easier approach to the situation and "assume" that the control files have gotten corrupted and the package management system is in an inconsistent state.
This can do no harm, and maybe all to the good !
Try terminal codes:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo rm /var/lib/apt/lists/partial/*
sudo mkdir -pv /var/lib/apt/lists/partial
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

```
update rebuilds the index files that were removed. and upgrade will update all installed packages to the latest versions that are in the software repository.

Advise us of the results.


I had a problem with Update Manager in Lucid Lynx (10.04) that was vexing me for *months*.  After a problematic, interrupted software update, Update Manager always showed "Download size: 207 KB", even no packages remained to be downloaded.  I executed the following two commands, restarting Update Manager after each one:
```

sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf

```
The first one didn't clear the condition, but when I started Update Manager after the second command, it reported "Your system is up-to-date" and it no longer showed the "Download size" message.:)

Thank you!!

UPDATE 2014-01-29
The problem came back.  Update Manager still thinks there are 207 KB of updates to install, and at the last update it showed "2 of 3 packages selected", but there were only two packages in the update. The problem with the phantom package is obviously elsewhere, so I'll need to keep looking.  At least I can temporarily clear the message using the above procedure.

---

### Post by Bashing-om on 2014-01-22
richard-smith7-gmail;

Still not to where I can give this proper attention,
Prod me with a "bump" to the thread if I should have a slip of mind or can not fine you in all my mess.

@ Andrew_P. Good deal !
That is an example of the forum at work !

[INDENT][INDENT]all for 1 and one for all
[/INDENT][/INDENT]

---

### Post by richard-smith7-gmail on 2014-02-01
still experiencing the same problem. I wonder whether there are disk errors that need fixing?

---

### Post by Bashing-om on 2014-02-01
richard-smith7-gmail; Hey !

I am back ...

Let's see if we can lay a finger on what is not happening.
From square 1 and building up to where the problem may lie>
Post the out puts of terminal codes - Between code tags- :
```

lsb_release -a
sudo apt-get update
sudo apt-get upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

still
[INDENT]ain't nothing but a thing
[/INDENT]

---

