---
title: "Alternative ways to install?"
date: 2023-07-24
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2023-07-24
I've spent the past six hours trying to install 22.04, but it always hangs or otherwise fails. And each time it is something strange and different from the previous time. The first time failed because I set up a 1GB EFI partition and the installer insisted that 1GB wasn't big enough. I kept raising it, but finally canceled when it wouldn't take 5GB. And it was definitely on the EFI partition setup, not / or /home. Just now on a new, fresh attempt I got as far as formatting the / partition, but after two hours I discovered that it had hung because of 'permission denied.' 

Before I give up and try OpenSUSE or something else, is there some way to get past all the glitches and just do an automated 'for sure this will work' installation?

---

### Post by ian-weisser on 2023-07-24
All the Ubuntu installers are designed and extensively tested (by many folks here) to be "for sure this will work".

And they do. They are famous for being easy, reliable, and compatible with most common hardware.

But if that's not working for you, then go right ahead and try something else.

---

### Post by guiverc on 2023-07-24
Ubuntu 22.04 LTS ISOs were available with the following installers

- ubiquity ; the default for Ubuntu Desktop & many of the *flavors*
- calamares ; used by some *flavors*
- subiquity ; used for Ubuntu Server
- *canary* installer as it was known then, now ubuntu-desktop-installer but not yet deemed *ready* for prime time & likely outdated (*original 22.04 media only*) but I'd skip that one even if you have or found an ISO to download

For 22.04; two different versions of `calamares` are available; if using an ISO with the outdated calamares; I'd suggest using a later (22.04.2) ISO that contains an updated calamares. Whilst I never encountered any issues with either, I'm aware that some did & thus the version of the installer can matter.

I have wanted in the past a Lubuntu system, but wanted to use the ubiquity installer, thus actually used a Xubuntu ISO for my install, then just converted the desktop post-install via package commands... ie. you can even pick your ISO/installer & fix issues later if you wish. 

How you write the ISO really matters, my default method has no issue, but I'm using a pure *clone* write without any re-format of the ISO thus have few issues. I've experimented with other options users have used & thus ran into problems end-users have reported; as both `calamares` and `ubiquity` can be *tricked* to write the boot loaders (inc. ESP) on incorrect devices where the ISO wasn't written to media correctly. I'll suggest to stick with documented methods of writing ISOs to media.

I've installed to ESPs as small as 300MB but my preference is 600MB, so I can't imagine issues with a larger one, but specific details matter, and the ESP must be a specific format/file-system or else problems are to be expected (*errors can always be misleading*).

I find all GNU/Linux systems about equal with installing; but what you do before you actual install (ie. *verify ISO, how written to install media, verifying that write to media etc*) really matter (*in my experience*).  You mentioned 22.04, but not which ISO/product or what installer you actually tried.

Myself I had great success with `calamares` & `ubiquity`, but as I don't install Server systems often I didn't use `subiquity`, and as already stated I'd not recommend using the *canary* installer if that's an 22.04 ISO you have (*you didn't specify, but it did exist even if it can no longer be downloaded*).


FYI:  All installers have *pros* & *cons* like anything... currently my favorite is still `ubiquity` as I know where its faults are, and when I need to just quit out & restart the app. The newer `calamares` may look 'pretty' but it's fragile too.. ie. all installers have quirks and when you use them rarely; be somewhat careful.. if you need to BACK UP thru dialogs because you made a mistake in a prior dialog, on some it's best to cancel the installation & start the installer again (*even with some after restart!*).  These quirks exist regardless of *distro* being used; eg. `calamares` is identical on Ubuntu ISOs to other distributions that also use it etc.. so switching to a different distro and using the same procedures will have the same results...

---

### Post by MAFoElffen on 2023-07-25
I would verify not just the installer image, but on boot of the installer, do a fast check that it has booted in the correct boot mode (UEFI or Legacy). That seems to be a recent/current problem, with some new users. (though you are far from being a new user) <-- Which that problem is very closely related to what Guiverc implied, on how the install media was created, and the BIOS Settings.

*** Didn't you have a good running 20.04 LTS install (besides your NAS), that you were looking at File Managers to rename video files, that then had a recent upgrade dependency problem? So Ubuntu was running on it for a long time with no problems. So I'm am thinking that it's not the hardware, but rather maybe the installer media.

---

### Post by John Jason Jordan on 2023-07-25
> **MAFoElffen said:**
> I would verify not just the installer image, but on boot of the installer, do a fast check that it has booted in the correct boot mode (UEFI or Legacy). That seems to be a recent/current problem, with some new users. (though you are far from being a new user) <-- Which that problem is very closely related to what Guiverc implied, on how the install media was created, and the BIOS Settings.

*** Didn't you have a good running 20.04 LTS install (besides your NAS), that you were looking at File Managers to rename video files, that then had a recent upgrade dependency problem? So Ubuntu was running on it for a long time with no problems. So I'm am thinking that it's not the hardware, but rather maybe the installer media.

It turns out that was not the problem at all, although it certainly seemed so. The computer did have 20.04. running fine, but I kept having broken packages. And the massively frustrating part was that none of the command line fixes did anything. Mostly the command ended with 'unable to continue due to broken packages.' (Not helpful!) The final fix was to upgrade to 22.04, which everyone said would surely resolve the problem. Well, the upgrade to 22.04 went well, but afterwards there were many, many broken packages, and I could do nothing. The long and the short of it is that the drives were failing (2TB Samsung SSD and 4TB WD spinny disk, both a bit over 5 years old). When I discovered that all my problems with broken packages became clear.

I disconnected both drives inside the case, and then tried to install to a 512GB USB 3.0 drive. I spent all day on this exercise, ultimately installing Mint, because Xubuntu just kept giving me random errors and failing. 

This morning I bought a new 2TB m.2 drive, installed it and, using the same Xubuntu ISO, installed it to the new drive. It's working, but lots of things need fixing. E.g., since I'm the only user I set it up to boot without requiring login. I also set power manager never to sleep, hibernate or shut down. No such luck. Every 15 minutes it goes into hibernation, locks the screen, and requires my password. Grrr. 'Hey, computer! I told you no <expletive> passwords!" There's probably a setting somewhere that I didn't find, but it will take hours to find it. A week or so from now I'll finally have a computer that is working.

Apologies. I'm frustrated. :(

---

### Post by MAFoElffen on 2023-07-25
LOL. No problems.

I've spend the morning adding a new SSD drive and re-installing one of my laptops from an LVM2 Volume Manager onto ZFS. Just finishing up the migration and taking the first snapshots.

I cannot say that it is not having problems this morning. Unfortunately, the same as you with it going into hibernation, when I have all the settings telling it not to. That started a few days, with gnome-control-center crashing. I have a bug filed for that. 

After I get done with the snapshots, I'll dive into that and see what I can find with mine.

---

