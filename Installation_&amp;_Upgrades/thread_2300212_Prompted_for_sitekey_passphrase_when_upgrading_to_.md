---
title: "Prompted for sitekey passphrase when upgrading to 15.10"
date: 2015-10-24
forum: Installation &amp; Upgrades
---

### Post by rtimai on 2015-10-24
I upgraded my HP Pavilion dv6 3012he from 15.04 to 15.10 tonight with no major issues, very impressed. 

Partway during the process I was prompted for a sitekey password for Tripwire, and had no clue what that was, as it was not recorded in my passwords list. However, the installation allowed skipping that step, with instructions for correcting it later. After the upgrade completed, I recalled that Tripwire was part of rkhunter (rootkit hunter) that I had previously installed. I followed the instructions for creating a new sitekey passphrase, which caused errors, and prevented rkhunter from starting (this is a console application that runs in Terminal.) I had to remove-completely rkhunter, sudo rm /etc/tripwire/*.* config files (which were not removed by the uninstall,) and then re-install rkhunter, which fixed it.

If you're prompted for a "sitekey passphrase" during your 15.10 upgrade, it's your sudo password. Don't try to change your sitekey passphrase manually as instructed.

Roger

---

