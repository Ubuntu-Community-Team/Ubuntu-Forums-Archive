---
title: "Broken Synaptics Package Manager ?"
date: 2006-11-13
forum: Installation &amp; Upgrades
---

### Post by jgcamp99 on 2006-11-13
I think I broke it.

I tried installing Panda desktopsecure and this error message comes up when I try to use Synaptics Package Manager:

[B][I]An error occured

The following details are provided:

E: The package desktopsecure needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.[/I][/B]

Then when I close that box, no packages are indicated.

I try to reload them, and this message comes up ?

[B][I]Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.[/I][/B]

I close that message box and this one appears after it:

[B][I]An error occured

The following details are provided:

E: The package desktopsecure needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
E: Unable to lock the list directory[/I][/B]

Stumped on this one, Please Help !

---

### Post by jgcamp99 on 2006-11-13
BTW, The deb package was provided thru Panda, I ran it an dit required that I have Edgy's 386 kernel option installed. It downloaded 2 files and Ubuntu installed it and added it to GRUB. If anyone knows what I did to this, maybe this helps too.

The first time Synaptics broke, I was instructed to "dpkg --configure to -a" in the terminal. SO I did it figuring it was good advices. Didn't seem to help any though.

---

### Post by jgcamp99 on 2006-11-14
Fixed, did a clean reinstall, tried some of the other steps I had researched, I couldn't reinstall and couldn't remove the software package/application that was locking Synaptics from working properly. New install had a few issues, but I resolved them and now only need to get the repository applications and a few other items to be back where I was. Probably need to learn more about system backups and restores in Ubuntu before I get ambitious again and try to install something I've never done before that isn't a repository provided application ?

---

