---
title: "Synaptic package manager not working, showing error"
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by sunnyengineeer on 2015-05-23
Hello,

When I try to open Synaptic package manager it shows the below error message"-

[COLOR=#ff0000]"E: Encountered a section with no Package: header[/COLOR][COLOR=#ff0000]E: Problem with MergeList /var/lib/apt/lists/ppa.launchpad.net_ffmulticonverter_stable_ubuntu_dists_trusty_main_i18n_Translation-en[/COLOR]
[COLOR=#ff0000]E: The package lists or status file could not be parsed or opened.[/COLOR]
[COLOR=#ff0000]E: _cache->open() failed, please report."

[/COLOR]I tried running sudo apt-get update through terminal, even that is not able to fix it! Can anyone please help me in solving this issue?

Thanks everyone

---

### Post by Vladlenin5000 on 2015-05-23
Please post the results of
```
sudo apt-get update
```

Are you running Lubuntu? What version?



Note: "apt-get update" won't fix anything but may give us clues about the problem.

---

### Post by Vladlenin5000 on 2015-05-23
**Additional Info**

I your previous [thread]("http://ubuntuforums.org/showthread.php?t=2203006") about Texlive you mentioned > I have only around 1.5 GB in my Lubuntu drive which can be used for it
This was in February. Is it the same situation? Could it be you're running out of free space?
-and-
Did you managed to install it? I have to ask since you didn't follow up your thread, not even to say thanks to the users who tried to help you... If you did then most certainly you're in a very bad place now. Please check your current free space and post back. Thank you.

---

### Post by sunnyengineeer on 2015-05-24
Sorry to reply late.

I have around 1 GB in the drive in which Lubuntu is installed. I have installed the softwares even when I had 0.5 GB space.

Regarding sudo apt-get update output ...here it is...see attached:-

---

### Post by Vladlenin5000 on 2015-05-24
You have several problems:

- It's recommended to have much more free space than what you currently have, regardless of the OS. As a side note, in the same scenario, Windows would be misbehaving and extremely slow. Ubuntu works but it may not have enough space to let APT operate (updates). This is the main problem and can potentially prevent the correction of other errors.
- You have several outdated/nonexistent PPAs that you should remove. This PPAs seem to have been carried out from an older xUbuntu version.
[B]ppa:natesm/ease
[B]ppa:upubuntu-com/office
ppa:joe-nationnet/seamonkey-dev[/B]
[/B]
Neither have versions for trusty (14.04), hence the errors. You should remove all and
```
sudo apt-get update
sudo apt-get upgrade
```

This is the first troubleshooting step and I wouldn't be surprised should the problem persist. Again, your main issue right now is the lack of space.

---

