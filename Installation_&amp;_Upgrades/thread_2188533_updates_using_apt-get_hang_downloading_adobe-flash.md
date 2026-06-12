---
title: "updates using apt-get hang downloading adobe-flashplugin"
date: 2013-11-17
forum: Installation &amp; Upgrades
---

### Post by dwreid55 on 2013-11-17
I did a search to see if anyone had posted this problem but didn't find anything. My apologies if this has been answered before.

Applies to version 13.04

When running apt-get to apply upgrades to my system everything proceeds normally until I reach this line:
*flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.327.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.327.orig.tar.gz)*
At this point, the process stalls and just sits there. I've waited for hours and it does not time out nor does it proceed. CTRL-C does not terminate the process. If I kill the process by closing the terminal window, it (of course) leaves the upgrade incomplete. If I attempt to run *sudo dpkg --configure -a* to complete the process it picks up where it left off and then stalls at the same line. 

As expected, running sudo apt-get install -f fails with the error [I]dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
[/I]
I can't seem to find a way to get around this problem. Can anyone help? 

I appreciate any advice. 

Thank you!

David

---- Additional information (update)

I have attempted the same process on a machine running version 12.04. I have the exact same problem and error. Both are running Google Chrome Browser stable release. However, I did note that the download being attempted references archive.canonical.com so I am assuming that the problem is on the Canonical end and not Google. 

Hope this extra info is helpful.

David

---

### Post by dwreid55 on 2013-11-17
I reset the DSL modem. I am able to ping the server. I can access Canonical servers for other updates and upgrades. I still have the same problem. 

Are there any other suggestions for how to get past this point and prevent it from trying this the next time I need to update/upgrade? 

Thank you!

David

---

