---
title: "Problems with GNOME Extensions after 12.04 upgrade?... Purge all, reinstall"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by kohoutek1 on 2012-04-27
After upgrading to 12.04 today, I had high hopes that I could get my GNOME Shell back to where I had it in 3.2. All extensions were broken, but that wasn't so bad. One of the first things I did was to get on the GNOME Extensions website to get the "updated" versions. 

Everything was going according to plan. But things turned sour after installing a batch of extensions and then rebooting the computer. The whole Shell crashed, leaving me with only the basic Metacity. Crash alerts flashed on the screen faster than I could answer them: "Ubuntu 12.04 has experienced an internal error." When I clicked the Apport button, I got this: The problem was not reportable because this is not officially supported software, or words to that effect. 

I rebooted into Gnome Classic and began troubleshooting. The fix was easy:  

(1) Go to the two directories where extensions are stored and delete all of them. Move them to the Trash and empty the trash. 

(2) Use Synaptic to make sure no gnome-shell-extensions are still lurking somewhere.

(3) Reboot

(4) Log into GNOME, not Classic

(5) Go to GNOME Extensions website and begin installing those that are available. The list is only about half as long as it was under 3.2.

I hope this solves problems for any one who's using GNOME Shell 3.4 on Ubuntu 12.04

---

