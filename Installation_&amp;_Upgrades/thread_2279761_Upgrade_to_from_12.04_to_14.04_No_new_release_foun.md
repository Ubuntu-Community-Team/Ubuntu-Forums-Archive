---
title: "Upgrade to from 12.04 to 14.04 No new release found"
date: 2015-05-25
forum: Installation &amp; Upgrades
---

### Post by Evan_B._Howard on 2015-05-25
I am trying to upgrade my Dell XPS13 with Ubuntu 12.04 pre-installed to 14.04.2. I updated, then did   sudo do-release-upgrade.
What I saw was:
Checking for a new Ubuntu release
No new release found

That was all. I tried this twice. Then I checked my own version with   lsb_release -a
What I saw was:
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04.5 LTS

Ideas or Suggestions? I have only been working with Ubuntu for a few months so there is probably something I am missing.
Thanks.

---

### Post by grahammechanical on 2015-05-25
You need to go to System Settings>Software & Updates>Updates tab. You might find that the panel labelled Notify me of a new Ubuntu version is set to Never. Or to Any new version. Which will not work as the next version up from 12.04 is 12.10 and that has reached end of life and the upgrader utilitiy will not let us upgrade to an end of life version. You need it to be set to For Long Term support versions.

Regards.

---

### Post by Evan_B._Howard on 2015-05-27
Thank you. I did not find what you described under System Settings (my computer has no tab for software under System Settings). However, I did discover a Settings button within Update Manager and in there it had the very options you mentioned. I set my option to For Long Term Support, ran Update Manager and it is now offering me the option of updating to 14.04. I always appreciate the help of this forum.

---

### Post by grahammechanical on 2015-05-27
I am glad that you found the solution. It has been a long time since I used 12.04 and things change. I have been seeing Software & Updates for so long I forgot it was once called Software Sources. Once you get to 14.04.2 have a look around System Settings. You will see improvements. We do not have 4 workspaces by default any more. System Settings>Appearance:>Behaviour is where we enable work spaces.

Regards.

---

