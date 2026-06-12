---
title: "Upgrade Failed, GRUB Corrupted"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by Gibran on 2007-04-23
Hello everyone,

I was upgrading to Feisty when we had a power outage and when I tried turning the PC on I would get a "Grub>" prompt. I have the Feisty LiveCD, but I don't know which files I would need to replace or if there is another way to restore my system. I wouldn't like to have to do a fresh install because it's taken **a lot of time** to customize Ubuntu to my liking and solve every issue that has come up... Thanks in advance!

---

### Post by pepsi_max2k on 2007-04-23
if it failed while upgrading there's probably little you can do as many files for the os could be missing. sounds like it's deffinately missing the /boot/grub bits, then likely also /boot, so don't expect to be able to boot much even if you could get grub working. you could try and backup your /home partition somewhere, if it's still there, via the live cd then clean install / restore files from /home. that should at least keep some of your old settings.

---

### Post by Gibran on 2007-04-23
I was hoping there would be a way to resume the upgrade somehow instead of just reinstalling...The home folder is still here, but it's not readable since I "do not have the necessary permissions". Is there any way to repair the system or something?? It'd REALLY suck to have to reinstall everything...(BTW, I'm dual-booting with Windows XP)

---

### Post by Gibran on 2007-04-23
Strangely enough, after booting from LiveCD GRUB is working! However it tells me that X-server is not properly configured and I am able to log in using the console mode, which makes me think perhaps the drivers are not properly configured and the system is still salvageable. Any ideas?

EDIT: The error in the X Server Output is "No Screens Found"

---

