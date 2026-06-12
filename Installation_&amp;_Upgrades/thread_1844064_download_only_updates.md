---
title: "download only updates"
date: 2011-09-14
forum: Installation &amp; Upgrades
---

### Post by dsa42 on 2011-09-14
I have had problems previously when the download for installing updates failed.  Since then, I have set the option in the update-manager to &quot;download only in background,&quot; and then I install them after they have been downloaded successfully.  Sometimes, though, I want to get the download going, and the background downloaded seems to take forever - even with nothing else on the system running.  There don't seem to be any options in the GUI to force the download to start without installation.  In the apt-get command line, there is a &quot;download-only&quot; option, but I am inferring from the man page that this is only for downloading specific packages.  My question is: Is there any way to force downloading of only the smart updating packages and not to install them?

---

### Post by zvacet on 2011-09-22
You have GUI option for download only.You will see it in synaptic after **refresh>mark all updates>aplay** and then at the bottom you will see download only and check that.

---

