---
title: "Update Script freezes on removal of cups-pdf"
date: 2013-04-21
forum: Installation &amp; Upgrades
---

### Post by kevdog on 2013-04-21
So I'm in the middle of upgrading Ubuntu versions using the distribution upgrade gui -- things going fine -- until the clean up stage.  I'm prompted to remove like 54 packages.  I peruse the names of the packages and they all seem reasonable to remove and I click accept.  The second package the script tries to remove cups-pdf -- it appears the script is stuck on.  Does cups-pdf run as a service?  Is it waiting for the service to be stopped?

---

### Post by breezypt on 2013-04-21
I would shut down my printer. Even just unplug it form your computer. It is something to do with your printer and the update. So you may be able to save yourself the agravation of reformatting, by just turning off the darn printer...

Hope this helps a little, I feel your pain I've been through at least 10 reformats after updates. I realize an upgrade is different form an update, but updates shoud not kill your OS. And for wht its worth a cups package should not be causing you the problems it is. If it was a kenel I could understnad it but a darm printer package, is insane...

---

### Post by kevdog on 2013-04-21
Just a heads up to anyone that runs into this problem -- the update script froze awaiting for removal of the script.

I opened up a terminal and typed a:
sudo ps -ef | grep cups

and then just killed the job number associated with this package removal.  The script then just ran as normal except the cups package was not removed.  The upgrade went as expected.  I have yet to reinstall the virtual pdf printer through cups however.

---

