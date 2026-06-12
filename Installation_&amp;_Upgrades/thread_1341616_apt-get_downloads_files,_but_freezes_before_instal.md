---
title: "apt-get downloads files, but freezes before installing"
date: 2009-11-29
forum: Installation &amp; Upgrades
---

### Post by dallingham on 2009-11-29
I'm trying to help a friend who had a botched attempt to upgrade from 8.10 to 9.04 (on his way to 9.10). apt-get will download updates, but freezes before installing them. All the downloaded .deb files can be found in /var/apt/cache/archives

After the download is complete, there is no further output from apt-get. Synaptic and update-manager also fail to upgrade the files. Installs of new packages also fail, only downloading and never proceeding to the actual install.

After the files are downloaded, I can install them using dpkg. There are no errors reported from any of the tools. There are no broken packages reported.

Any suggestions on what may be wrong would be appreciated. Without any error messages, I'm not sure how to proceed.

---

### Post by lemming465 on 2009-12-12
Check the files in /var/log for error messages too, particularly /var/log/messages.

Does *sudo dpkg-reconfigure -a* help any?

---

