---
title: "Lucid: Software Sources still showing Karmic"
date: 2010-04-27
forum: Installation &amp; Upgrades
---

### Post by donsy on 2010-04-27
After doing clean installs of the last two Ubuntu Releases, Jaunty and  Karmic, I decided to try an upgrade to Lucid. The upgrade went well and  I'm satisfied with it, however I have a question about the repositories. All the sources in /etc/apt/sources.list correctly point to  Lucid, but in Software Sources / Other Software I still see references  to Karmic. Is this something to be concerned about? Can I (or should I)  change them to Lucid?

---

### Post by ghostborg on 2010-04-27
Only if they're checked. Unchecked they are disabled and just left behind from the upgrade for people who might need them for future reference.
Usually only the installation repositories are used during an upgrade and you might have seen a message pop-up and inform you that some of the repositories are being disabled for the upgrade. Sometimes you can edit the Distribution line and change karmic to lucid , only if it is a valid repository tho.:)

---

