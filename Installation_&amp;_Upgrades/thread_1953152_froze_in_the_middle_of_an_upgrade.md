---
title: "froze in the middle of an upgrade"
date: 2012-04-05
forum: Installation &amp; Upgrades
---

### Post by pdkfjz on 2012-04-05
i am upgrading my 10.04 ubuntu 32 bit to 11.10, at the it freezed at the "installing the upgrade" step with dropbox upgrade at 50%. What do i do now as shutting or restarting the computer will result with the system being broken?

pic attached

[IMG]http://1.bp.blogspot.com/-FHgCZ6qFPXU/T34G5SH8uFI/AAAAAAAAAEM/oa2tCO_Mmto/s1600/Screenshot+at+2012-04-05+23:55:47.png[/IMG]

---

### Post by darkod on 2012-04-05
If it's completely frozen, I guess you don't have much choice.

If you restart and at least can boot recovery mode, you can run:
sudo dpkg --configure -a

to finish configuring all pending packages.

If even recovery doesn't boot, you could try chroot-ing into the install and running the dpkg command. Hopefully it will work.

---

### Post by LinuxFan999 on 2012-04-05
Upgrading through the update manager is not recommended. The upgrade process is more likely to break Ubuntu than a hard reset. I recommend doing a clean install of Ubuntu 11.10. Remember to back up your data first.

---

### Post by darkod on 2012-04-06
Also, it could be a typo but you shouldn't be able to upgrade from 10.04 to 11.10 directly. You can only upgrade directly from LTS to LTS, otherwise you need to go version by version.

A direct upgrade should be possible with the cd but you seem to be doing it online. You would need to go 10.04 -> 10.10 -> 11.04 -> 11.10.

It was better to wait for 12.04 LTS to come out and upgrade directly to 12.04 if you wish to upgrade. Since you stuck with 10.04 so long, I see no reason to upgrade to 11.10 few weeks before 12.04 is released.

---

### Post by LinuxFan999 on 2012-04-06
> **darkod said:**
> Also, it could be a typo but you shouldn't be able to upgrade from 10.04 to 11.10 directly. You can only upgrade directly from LTS to LTS, otherwise you need to go version by version.

A direct upgrade should be possible with the cd but you seem to be doing it online. You would need to go 10.04 -> 10.10 -> 11.04 -> 11.10.

It was better to wait for 12.04 LTS to come out and upgrade directly to 12.04 if you wish to upgrade. Since you stuck with 10.04 so long, I see no reason to upgrade to 11.10 few weeks before 12.04 is released.
I noticed that the OP is actually running Ubuntu 11.04 (look at the screenshot).

---

### Post by Borg on 2012-04-06
All I seem to keep getting is



> The connection to the daemon was lost. The background daemon probably crashed.

---

