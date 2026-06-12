---
title: "Can't Start Post-Install Programs in 10.04 LTS"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by deSoDa on 2010-10-02
I'm a Ubuntu Desktop newbie, and I wiped XP Media Center off my old HP Pavillion Dv8000 last night to install 10.04 LTS.  With very little tweaking, I got everything to run right including wireless, but now I notice that I can't run any new (post-install) programs that I install through Ubuntu Software Center.  In fact, I haven't tried installing any other way, but all software that was part of the default installation works fine, but these programs won't run:

[LIST]
[*]VLC Media Player
[*]Skype
[*]KStars
[/LIST]

When I click on the programs to run them, the other apps slow or freeze for 30-45 seconds as if the computer is contemplating starting them, and then nothing.  No errors, no shell or blank window - nothing.  They just don't run.

I only created one user account at O/S install and as far as I can tell is the SU, so I can't see it being a permissions issue.

What can I look for to fix this?

-- deSoDa

---

### Post by decoherence on 2010-10-02
Try running the programs from the command line with Applications -> Accessories -> Terminal and type 'skype' or 'vlc'. You should get some kind of error then.

---

### Post by garvinrick4 on 2010-10-02
I imagine you have not installed any codecs,flash,java and updated your install.
You have 699 or so meg on the CD or USB install and rest is in repositorys.
Go to System/Admin to software sources and open. Make sure all repositories are checked
and add medibuntu (google medibuntu Ubuntu to get how to's). Once repositories are all there you can update.
```
sudo apt-get update
``````
sudo apt-get install ubuntu-restricted-extras && sudo apt-get update && sudo apt-get upgrade

```ubuntu-restricted-extras gives you the restricted packages of codec's and flash and java and others. The update and upgrade gives you all the latest packages of ubuntu-desktop
If you have already installed all restricted packages, then I say uninstall and then clean system and reinstall. Will fetch new packages from repository.
```
sudo apt-get purge (package)
``````
sudo apt-get clean
``````
sudo apt-get install (package)
```

---

### Post by deSoDa on 2010-10-02
Well that's a start...I get...

Bus error

...for VLC, Skype and KStars.  But I just remembered that I installed Chromium and Filezilla last night and they've been working fine.

Not sure (meaning NO clue) how to fix a bus error in Linux.

-- deSoDa

---

### Post by deSoDa on 2010-10-08
Well I finally got it figured out.  Simply put, the HD was dying and had some bad sectors.  Ubuntu didn't catch it on install, but after I replaced the drive with a new one, and then reinstalled Ubuntu, these problems went away.

Thanks to everyone who replied.

---

