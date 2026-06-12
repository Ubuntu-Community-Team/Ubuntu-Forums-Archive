---
title: "Dist-upgrade doesn't pull down new packages?"
date: 2008-07-25
forum: Installation &amp; Upgrades
---

### Post by nightmarestreet on 2008-07-25
Hi folks,

Is it true that aptitude dist-upgrade simply upgrades existing packages but won't pull down any new ones? Does the graphical "update manager" solve this problem?

---

### Post by avtolle on 2008-07-25
Both will only update packages that are already installed. To install new packages from the repositories, use the Add/Remove feature under Applications, or Synaptic (System>>Administration>>Synaptic Package Manager).

---

### Post by nightmarestreet on 2008-07-25
So what is the correct way of upgrading every 6 months to the new release? Obviously I'd like to get the new packages in addition to upgrading my existing ones...

---

### Post by Sef on 2008-07-26
> So what is the correct way of upgrading every 6 months to the new release? Obviously I'd like to get the new packages in addition to upgrading my existing ones...

The best way is a clean install, i.e. reinstall.  There are fewer problems that way than by with the update manager.  However, you have to reset all your settings.

---

### Post by steveneddy on 2008-07-26
> **Sef said:**
> The best way is a clean install, i.e. reinstall.  There are fewer problems that way than by with the update manager.  However, you have to reset all your settings.

I agree. Total reinstall after a backup of /home is the way to go.

---

### Post by kostkon on 2008-07-26
> **nightmarestreet said:**
> Hi folks,

Is it true that aptitude dist-upgrade simply upgrades existing packages but won't pull down any new ones? Does the graphical "update manager" solve this problem?

I don't know about aptitude but better do it using the Update Manager.

The upgrade process will update your current packages, will install any new ones needed for the new version and will obviously remove any that are not needed anymore.

---

### Post by nightmarestreet on 2008-07-26
Ahh, damn. I was hoping that wouldn't be the case.

Although I suppose I can do an actual reinstall for every LTS release, and use update manager for the others.

Anyway thanks for clearing that up :)


EDIT: Are you sure about that Kostkon? That conflicts with what Avtolle said...

---

### Post by hansdown on 2008-07-26
My mantra is "a clean install fixes all". Just my preference.

---

