---
title: "puzzled by upgrade to 22.04"
date: 2023-09-18
forum: Installation &amp; Upgrades
---

### Post by pjstock on 2023-09-18
I am trying to upgrade a system currently running 20.04 to 22.04
while running in 20.04 I get prompts to "Upgrade" after which I click on "INstall Now" but.... nothing seems to happen.

I then try under Settings > About > Software Updates but that only seems to set setting for updates. it doesn't seem to actually DO any updates. (as my only options there seem to be Revert and Close)

So, I thought I would try upgrading off a 22.04 bootable USB stick
in some How Tos I've seen they seem to show an "Upgrade" option (along with "Try It" and "Install")

Mine only shows "Install" and a scary message about deleting the entire disk....

So I choose "Something Else" which shows me my current partitions.
I assumed that I should choose the location of my current 20.04 install (sda3/ext4)

but I fail on a "No Root File System Is Defined"

and at this point I am lost.

what am I doing wrong? what should I be doing?

---

### Post by grahammechanical on 2023-09-18
In Software & Updates>Updates tab is Notify me of a new Ubuntu version set for Long Term Support versions? If it is I do not understand why the option to upgrade to 22.04 does not start the upgrade. Internet connection issue? You would have checked that I am sure.

I use 20.04 and get that upgrade message but I do not accept it. So, I do not have recent experience of what should happen. Sorry.

Regards

---

### Post by TheFu on 2023-09-18
I've never used the GUI to move between releases.

Here's what I'd do.
In 20.04, run 
```
sudo apt update
sudo apt full-upgrade
reboot
``` and login again.
```
sudo do-release-upgrade

```Wait 2.5 hours, answering questions as they come up.  Too bad we can't just walk away.  About every 10 minutes, a question will be asked and the process will stop until answered. It is a bit of a pain.

Before stating, ensure there's 400MB free in /boot/.  If not, clean up /boot/ so there's only 2 kernel versions there.

And it should go without saying that upgrades like this are like swapping out a car engine, so always, always, always create a backup of all the stuff on the system that you aren't willing to lose. If you cannot restore the files from the backup and don't 100% know it, figure that out first.  Bad things happen sometimes.

---

### Post by pjstock on 2023-09-18
I spotted command line instructions that looked like those in a How To.
Tried them.
failed

But, I'll try it again .
maybe I missed the Reboot step.

---

### Post by pjstock on 2023-09-18
there were a few errors in the first two steps.

but doing "Sudo do-release-upgrade"

I get a message " please install all available upgrades for your release before upgrading"

so now I have no idea where I am.....

---

### Post by TheFu on 2023-09-18
If you don't have enough space, you don't have enough space.

If you choose to "To something else", then you are expected to setup multiple partitions, size them appropriately, say which file system they should be formatted (or not) using, etc.  For an upgrade, "do something else is not what you want.

To clean up storage, there are a few things that can be done.  You can look up the specific command, since I'm working from memory and might get them wrong.
Run apt autoremove, apt autoclean, set the systemd logs (journalctl) to be 50MB, not 5GB, tell snap to delete extra copies of snaps. The default is 3 and the snap team decided we shouldn't be allowed to have 1 copy of a snap for some reason, but that would reduce the snap package sizes by 1/3rd which can add up if you haven't been careful to avoid snap packages.

Obviously, deleting extra files data that aren't needed would be good too.

BTW, this command 
```
lsblk -e 7 -o name,type,fstype,size,FSAVAIL,FSUSE%,label,mountpoint
```
provides a nice overview of real storage, file systems and how full it is and where it is mounted.  GUI tools don't do that as compactly.  If you post it, you must wrap it in "code tags" or the columns won't line up and it will be completely unreadable.

---

### Post by pjstock on 2023-09-18
> **TheFu said:**
> If you don't have enough space, you don't have enough space. 
i never got any notice that I was short of space.
and I assumed that 30gb was sufficient.
should it not be?

> **TheFu said:**
>  If you choose to "To something else", then you are expected to setup multiple partitions, size them appropriately, say which file system they should be formatted (or not) using, etc.  For an upgrade, "do something else is not what you want. 


the options I was presented were: "Do Something Else" or "Erase the drive and reinstall". (not the friendly "Upgrade?")
the 2nd choice seemed severe and risky so I explored Do Something Else.

But I will try your other suggestions.
thank you.

---

### Post by TheFu on 2023-09-18
> **pjstock said:**
> there were a few errors in the first two steps.

but doing "Sudo do-release-upgrade"

I get a message " please install all available upgrades for your release before upgrading"

so now I have no idea where I am.....

If there is a multi-step process and 1 fails, STOP!!!!!!!!!!!!!!!!   Fix that step before going forward.

---

### Post by pjstock on 2023-09-18
this is what I get after trying: 
sudo apt update

[code]
Get:1 http://dl.google.com/linux/chrome/deb stable InRelease [1,825 B]
Err:1 http://dl.google.com/linux/chrome/deb stable InRelease                   
  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
Hit:2 http://security.ubuntu.com/ubuntu focal-security InRelease
Hit:3 http://ca.archive.ubuntu.com/ubuntu focal InRelease     
Get:4 http://ca.archive.ubuntu.com/ubuntu focal-updates InRelease [114 kB]
Hit:5 http://ca.archive.ubuntu.com/ubuntu focal-backports InRelease
Fetched 114 kB in 11s (10.6 kB/s)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
489 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/chrome/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease  The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
W: Some index files failed to download. They have been ignored, or old ones used instead.
[/code}

---

### Post by pjstock on 2023-09-18
and I, I am afraid, have no idea what this means.

```

W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://dl.google.com/linux/chrome/deb stable InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
W: Failed to fetch http://dl.google.com/linux/chrome/deb/dists/stable/InRelease The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4EB27DB2A3B88B8B
W: Some index files failed to download. They have been ignored, or old ones used instead.

```

---

### Post by TheFu on 2023-09-18
You setup an external repo, probably for Google-Chrome.  Remove that and start over from step 1.  STOP if there are any errors in any steps.

As part of an OS upgrade, 3rd party repos are disabled, so doing this won't be bad anyway.

---

### Post by pjstock on 2023-09-19
thank you for your patience and help.

How would I remove that failed Chrome install?
I tried to Uninstall from the GUI "Ubuntu Software" but after a reboot, when I try to "terminal" sudo apt update I get the same errors.
so I expect I have to do removal at the command level, and I do not know how to do that.

Peter

---

### Post by TheFu on 2023-09-19
> **pjstock said:**
> thank you for your patience and help.

How would I remove that failed Chrome install?
I tried to Uninstall from the GUI "Ubuntu Software" but after a reboot, when I try to "terminal" sudo apt update I get the same errors.
so I expect I have to do removal at the command level, and I do not know how to do that.

Peter

I hope you haven't been waiting for an answer.

Reverse whatever you did to add that repo.  It didn't magically happen.  Someone manually setup it up.  Undo that.  I'd never put software from Google on any of my Linux systems.  Heck, I don't even want google software on my Android devices.  Anyway, you'll need to figure this out.  I suspect there's a repo manager GUI tool. Alas, 

I don't use a GUI for this stuff and the way I'd do it is prone to errors by people not used to managing text config files. Best for you to search for a way to do it.  Perhaps the _Ubuntu Desktop Guide_?

---

### Post by pjstock on 2023-09-19
I regret having abandoned Cobol and Fortran.
Now THAT was a pure era of computing science.

I have never (as far as I can recall) installed software via Terminal. I am not that clever.
I have only installed software via the GUI Ubuntu Software.
so if I tried and failed to install Chrome it would likely have been there.
so, I thought that UNinstalling it there would clean things up.
doesn't seem to have.

Hey, thanks for your patience. It really isn't the end of the world that I go from 20 to 22. 20 is just fine.

my other option i guess is to just blow everything away and install 22.04 over everything.
there is nothing crucial that I need to save or that I cannot rebuild.
it just seems inelegant.

---

### Post by #&amp;thj^% on 2023-09-19
> **pjstock said:**
> 

How would I remove that failed Chrome install?

so I expect I have to do removal at the command level, and I do not know how to do that.

Peter
```
sudo rm /etc/apt/sources.list.d/google-chrome.list

```
Now run your update/upgrade again.

---

### Post by TheFu on 2023-09-19
> **pjstock said:**
> I regret having abandoned Cobol and Fortran.
Now THAT was a pure era of computing science.
My first compiled language was FORTRAN66.  Never used it again after that class. Never used FORTRAN in the real world either, though I did use it all through college. It was expected for engineering students.

Never touched or have I even seen Cobal. Heard that a billing system was written in it at one company.

> **pjstock said:**
> 
I have never (as far as I can recall) installed software via Terminal. I am not that clever.
I have only installed software via the GUI Ubuntu Software.
so if I tried and failed to install Chrome it would likely have been there.
so, I thought that UNinstalling it there would clean things up.
doesn't seem to have.

Hey, thanks for your patience. It really isn't the end of the world that I go from 20 to 22. 20 is just fine.

my other option i guess is to just blow everything away and install 22.04 over everything.
there is nothing crucial that I need to save or that I cannot rebuild.
it just seems inelegant.

The terminal is stupid, not clever, but like any skill, it takes practice to use.  OTOH, GUI programs are often created by programmers who don't really know what they are doing and leave cruft behind ... like they will add repos as part of the software install, but not remove those same repos when the software is removed.  Sadly, that is how GUI programmers usually think.  They are 1-way thinkers and don't consider removing most of the time.

I see 1fallen has answered.  That looks reasonable to remove a PPA. Ought to do what you need.

---

### Post by pjstock on 2023-09-20
That was VERY helpful.
thank you.
things seem to be moving forward.

---

