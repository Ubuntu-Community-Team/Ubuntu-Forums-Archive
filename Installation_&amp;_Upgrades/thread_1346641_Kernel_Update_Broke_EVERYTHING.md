---
title: "Kernel Update Broke EVERYTHING"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by cfree220 on 2009-12-05
Hi

I'm running Ubuntu 8.10 32-bit on a Dell XPS M1530. This morning I received a notification of new updates (kernel update), which I installed. Before restarting, I had noted that the Google search field in Firefox 3.0.15 was not responsive.

After rebooting, I found that several of my programs and  settings were not functioning properly:

Gnome-do: Did not load on login and could not be started from program menu.

Dropbox daemon: Did not start with login and could not be started from program menu. A few minutes into session, I received a popup prompting me to install the daemon. When I clicked ok, it brought up a download window, which did not show any progress, even after several minutes.

Firefox: Lost all bookmarks and saved login information. Search bar still not functional. Could not log into facebook (did not test with other sites; I am currently using Galeon).

Thunderbird: When launched, program issued configuration prompts.

Metacity: All stored wallpapers removed from collection. Was not able to switch between the three that remained.
_______________________________________________

Yesterday I updated two applications to newer versions (which were not packaged with Ubuntu). I added the Pidgin repository, allowing me to upgrade to version 2.6.3 (from version 2.5.2). I also downloaded and installed the most recent version of gnome-do (version 0.8.2 to improve plugin performance/gain compatibility with Pidgin DBus extension).

I tried booting using the previous kernel (I'm not sure on the kernel versions.... if anyone can instruct me on how to determine the available kernels on my system...). None of the problems were resolved by doing this.

Can anyone point me towards a solution? I need to either a. figure out how to get everything working with the new kernel, or b. figure out how to revert to a previous version and hope that removing the new version (rather than simply booting using the previous version) solves the issues.

---

### Post by cfree220 on 2009-12-05
I determined that the issue was caused by the most recent version of Pidgin (or by the combination of Pidgin and Gnome-do). Removing these repositories, removing the applications, and reinstalling resolved the issue.

---

