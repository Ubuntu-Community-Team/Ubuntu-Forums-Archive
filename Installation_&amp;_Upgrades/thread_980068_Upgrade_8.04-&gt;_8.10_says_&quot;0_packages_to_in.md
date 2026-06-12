---
title: "Upgrade 8.04-&gt; 8.10 says &quot;0 packages to install&quot;"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by gwi on 2008-11-12
I tried to upgrade Ubuntu 8.04 to 8.10 (after having installed all updates for 8.04, and rebooted twice).
What happens is:
[LIST]
[*]I start the update manager;
[*]I click on the "upgrade" button;
[*]some kind of release note is shown;
[*]I click on the "upgrade" button;
[*]two files are downloaded (called the upgrade program);
[*]I am asked for my password;
[*]nothing more, no errors, no windows.
[/LIST]

I then tried it using the command line:
[LIST]
[*]run sudo aptitude update;
[*]run sudo aptitude dist-upgrade;
[*]aptitude says 0 packages have to be removed, update or installed.
[/LIST]

I tried the same after disabling third party repositories, but that didn't change anything.

What's wrong here?

---

### Post by Dazed_75 on 2008-11-12
Look at Software Source in the System menu.  Go to the updates tab and in a list box near the bottom you may find it shows to only do upgrades to LTS releases.  If so, you can change that to Normal releases and then try the update manager again.

---

### Post by gwi on 2008-11-12
I already did that, otherwise the update manager would not have shown the "upgrade" button.

---

