---
title: "Discover tray icon shows 'Up-To-Date' when updates are available"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by accounts0 on 2017-10-26
The tray icon says green checkmark & when I click it it says there's 1 update available. But when I click the 'Update' button & Discover launches it shows there being more than 1. Same in Synaptic.

Screenshot:
[https://imgur.com/a/P1wAs](https://imgur.com/a/P1wAs)

---

### Post by vasa1 on 2017-10-27
Does this happen frequently or only today?

---

### Post by accounts0 on 2017-10-27
> **vasa1 said:**
> Does this happen frequently or only today?

Happened when I was using KDE Neon User Edition, but never on this box until just recently.

Since it's not always on to run unattended-upgrades properly I have a cron job that runs 'aptitude update' every 30 minutes, & I used to occasionally see the icon turn red all of a sudden then I'd take care of it right then. But today this isn't happening. What I saw after expecting a red icon there is how I found out its not right anymore.

---

### Post by vasa1 on 2017-10-27
There may have been issues today. I too didn't see updates available. But after checking in konsole, there they were:```
Start-Date: 2017-10-27  09:31:35
Commandline: apt-get dist-upgrade
Requested-By: vasa1 (1001)
Upgrade: libgnutls-openssl27:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), grub-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), google-chrome-stable:amd64 (62.0.3202.62-1, 62.0.3202.75-1), grub2-common:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), grub-efi-amd64-bin:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), grub-efi-amd64:amd64 (2.02~beta2-36ubuntu3.12, 2.02~beta2-36ubuntu3.14), grub-efi-amd64-signed:amd64 (1.66.12+2.02~beta2-36ubuntu3.12, 1.66.14+2.02~beta2-36ubuntu3.14), libgnutls30:amd64 (3.4.10-4ubuntu1.3, 3.4.10-4ubuntu1.4), wget:amd64 (1.17.1-1ubuntu1.2, 1.17.1-1ubuntu1.3)
End-Date: 2017-10-27  09:33:01

```

---

### Post by Impavidus on 2017-10-27
> **accounts0 said:**
> 
Since it's not always on to run unattended-upgrades properly I have a cron job that runs 'aptitude update' every 30 minutes.

Shouldn't be necessary. Ubuntu is well aware that most computers aren't on 24*7 (and most that are, are wasting energy), so the unattended upgrades don't run at a fixed time of day using cron. Instead, they run at a random number of minutes after boot.

I don't know if it applies here, but have you read about [phased updates](https://wiki.ubuntu.com/PhasedUpdates)?

---

### Post by accounts0 on 2017-10-27
> **Impavidus said:**
> the unattended upgrades don't run at a fixed time of day using cron. Instead, they run at a random number of minutes after boot.


```

designed to be run from cron (e.g. via [/etc/cron.daily/apt]("file:///etc/cron.daily/apt"))

```
I'm actually not sure I got it configured properly, since I didn't understand how to do this part- my crontab & sudo crontab didn't include anything like this by default that I could uncomment, & I think I read somewhere that the cron based scheduler was obsoleted by a systemd timer of some sort that I had no desire to get sucked into trying to figure out -likely over the course of days, lol! I just put it off & make clunky workaround scripts. 

> **Impavidus said:**
> but have you read about phased updates?
No, but that looks interesting. I wonder how they handle pushing urgent updates like for heartbleed, etc. Hopefully there's no delay there. I see it only applies to the "Update Manager" update manager, & not the "Discover" update manager that's standard in Kubuntu. I installed it to have a look & it's not immediately clear how I'd swap out Discover for Update Manager. There's no section to choose from in "'System Settings' > 'Applications' > 'Default Applications'", where I'd expect to see an entry in the left column to select which system tray package updater to use/launch by default. I'll just stick with Discover since it's integrated & at least the tray icon works, which seems difficult for more apps than I'd expect. eg. I have to pin an old Thunderbird Mail to run an old system tray extension that hasn't been updated in years. :-(

---

### Post by accounts0 on 2017-11-05
bump

---

