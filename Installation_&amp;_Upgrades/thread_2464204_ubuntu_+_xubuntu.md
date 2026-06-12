---
title: "ubuntu + xubuntu?"
date: 2021-06-26
forum: Installation &amp; Upgrades
---

### Post by mechanic on 2021-06-26
I'm trying to setup a new machine here. Now I'm torn between using the default Ub desktop, or installing & using the Xubuntu version (of 21.04 latest).

Now in order to keep options open the choice is either dualboot or have both variations available as alternative sessions. The second would mean less disruption to the existing default setup. Why not boot to Xubuntu you ask? I'm not impressed with the Xub. setup shown when I run the live DVD. The main issue I've had to start with is the visual problems is dealing with scaling on a high definition monitor. Ubuntu was able to set itself up from the word 'go' to work with a scale value of 2 on the desktop (impressed!).  So, should I:

(1) Use Gparted to shrink the existing Ub partition, and install Xub from the live DVD. But then what's the current thought on the best way to setup Grub for dual booting? Or:

(2) Install xfce4-session in the existing Ubuntu system and choose the running version at login - does that work? 

Thanks for any thoughts.

---

### Post by yancek on 2021-06-26
Do you have an EFI machine?  I don't use Xubuntu but many of the Ubuntu derivatives use an ubuntu directory in the EFI partition and if that is the case with Xubuntu, it would overwrite the already existing ubuntu directory there so you need to check at the Xubuntu site to determine that.  There are ways around this but that would be your first step.  This would not be a problem if you keep Xubuntu as it should show an entry for your Ubuntu in the grub.cfg menu but if you decide note to keep Xubuntu, it would be a problem.

---

### Post by oldfred on 2021-06-26
Its your choice, but I prefer not to have two different desktops in one install.
Years ago I did that and could not easily revert some settings. Minor things like names/labels but an issue.
I have many installs.
But Ubuntu will only use one UEFI boot entry and then from grub you choose other installs.
Typically last installed system, or last updated system with major update to grub will be default in UEFI.

I found easy to change /EFI/ubuntu/grub.cfg to be the UUID of my main working install. Or boot into preferred system & reinstall grub.
I have multiple installs, use a shared data partition, but keep /home inside each install. And have yet to fully allocated both SSD & HDD leaving room for more installs or data.

---

### Post by dddman on 2021-06-26
That was answered for me, here in this forum by TheFu.

It's better to create a new user and install the new desktop.  Thereby keeping them separated.

---

### Post by mechanic on 2021-06-26
That's an interesting thought. Boot into the Ubuntu system and choose a new account at  system boot login? This would setup a separate /home/username tree but retain the application/settings area. Thus different screen backgrounds, mail and Firefox prefs. But could they have separate applications installed - I think not?

---

### Post by dddman on 2021-06-26
Quote
"But could they have separate applications installed - I think not? "

Can't comment on that.  This advice was given to me after I bricked my system with too many desktops.  Later I removed that install and bricked Windows in the process.  That's not happening again, virtualbox is now in use.  I can now install any or all desktops.

---

### Post by &amp;KyT$0P# on 2021-06-26
> **mechanic said:**
> (2) Install xfce4-session in the existing Ubuntu system and choose the running version at login - does that work? 

This has a lot of display manager related issues.  Best stay away from this approach on any production system.

What aspects of Xfce do you like?  Depending on your answer you may have a third option: use Ubuntu session, but autostart some Xfce components in the Ubuntu session to result in a hybrid GNOME/Xfce experience.  I have tried this with xfce4-panel and it worked well for what I was seeking.

---

### Post by mechanic on 2021-06-27
OK, thanks for all the fish, I've gone with the separate partition route. This after more fuss in Xubuntu 21.04 than with the default Ubuntu initial install.  These systems still have issues with HDPI displays. The best detail on coping with such a display is in the Arch wiki (thanks to partner for pointers on that).
[https://wiki.archlinux.org/title/HiDPI](https://wiki.archlinux.org/title/HiDPI)
Shame that neither Dell nor Ubuntu seem to carry this level of support detail.

Interesting that grub-customizer is now in the repos, no fuss with the ppa.

---

### Post by him610 on 2021-06-27
>  Install xfce4-session in the existing Ubuntu system and choose the running version at login - does that work?
Yes, it does. A few weeks ago I had do some work on my wife's Ubuntu laptop while I am a longtime user of Xubuntu. Once a person gets used to doing things a certain way for many years then changing to another desktop environment (DE), sometimes gets a little frustrating. I mean it can be done, but you are not as efficient at doing things.  I installed Xfce4-session to my account, and that is what I boot into whenever I need to do something on my wife's computer.
You may plan to switch back and forth between DEs, but I don't think that is something I would do unless I had too. I guess you could say I am set in my ways.

---

