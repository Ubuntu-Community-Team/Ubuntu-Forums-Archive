---
title: "Help! Ubuntu 10.04 -&gt; 10.10 , No connection."
date: 2011-09-10
forum: Installation &amp; Upgrades
---

### Post by otterslide on 2011-09-10
I just upgraded from 10.04 to 10.10 using the procedure give on the Ubuntu site,

sudo apt-get install update-manager-core

edit /etc/update-manager/release-upgrades and set Prompt=normal

Launch the upgrade tool:

sudo do-release-upgrade
Everything went well, then it went down to reboot but never came back online.

I was doing this remotely on my VPS.

Future Hosting VPS support is telling me  they can connect to the server from the parent node, but I cannot connect from the  outside.  

They're saying it's a Ubuntu bug.. anybody experienced this?  I  can't find any info about it and I need my server back.

Not sure what needs to be done and it seems they don't know either.


Thanks for any help!

---

### Post by otterslide on 2011-09-10
Ok it looks like it was the startup scripts.. they're not starting any of the services, including SSH.

Any ideas or help?

I am not familiar with all the scripts that run at startup.

---

### Post by otterslide on 2011-09-10
Ok the problem is that the IP configuration got lost.

The host wants to reinstall the OS.  I'd rather configure the IPs manually, but I'm not sure which files are affected.  This is a VPS.. I found /etc/network/interfaces

is there anywhere else?

---

