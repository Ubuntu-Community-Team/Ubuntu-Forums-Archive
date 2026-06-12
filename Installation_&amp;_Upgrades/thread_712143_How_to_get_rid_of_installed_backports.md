---
title: "How to get rid of installed backports"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by botulismo on 2008-03-01
So, someone who was on my computer enabled the backports repository. I never would because it's broken programs and parts of my system before.

Well, I allowed ubuntu to do the automatic update thing and only afterwards realized it had updated many many packages to backported versions. Now there are all sorts of things wrong with my computer.

Is there any way to mass-downgrade, or at least identify which packages were backports so I can start the tedious process of doing it by hand?

---

### Post by bapoumba on 2008-03-01
Synaptic > File > History
You should see what has been installed by date.

Look into /var/log.
dpkg.log.1 shows the latest actions by dpkg. Older actions are under dpkg.log.2.gz, dpkg.log.3.gz etc, that you can extract to your desktop and look into. You will see which files have been upgraded.

From a terminal:
```
apt-cache madison <package_name>
```
Will tell you where the said package has been installed/upgraded from.

There may be a more direct way to do this all of these verifications, though..

Remove the backports from your sources.list or uncheck them from Synaptic and reload the file (reload button from Synaptic, or **sudo apt-get update** from a terminal).

We'll see from there which packages are coming from the backports and how you can downgrade (if possible at all).

---

