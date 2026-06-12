---
title: "Trouble with smbclient"
date: 2009-09-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jbslaw on 2009-09-21
I've done searches in this forum for smb and smbclient, but no threads deal with this issue.  I have an up-to-date installation of Karmic Alpha 6 that seems to run very well on my laptop.  The only hitch I've run into is accessing a windows printer attached to a network machine running windows XP.  It worked properly until an update a week or so ago.  

The Printer Configuration wizard fails to find the printer.  I set it up manually (both through the wizard and through CUPS) and a test print just sits there "processing."  I try to access the share using "smbclient -L //workgroup/server to no avail.  It eventually times out, reporting (NT_STATUS_UNSUCCESSFUL).  The printer share is properly set up and prints from Vista on the same machine as well has having printed from Karmic before the update.

I am not trying to mount any windows shares at this time, just print to a windows printer.

Any advice?

---

