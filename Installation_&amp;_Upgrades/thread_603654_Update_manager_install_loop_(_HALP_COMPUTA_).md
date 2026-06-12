---
title: "Update manager install loop ( HALP COMPUTA )"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by emullet on 2007-11-05
Upgraded to Gutsy last week. Installed the new VMWARE player package. It installed fine. Now the update manager tells me that it needs to update the VMWARE player package constantly. I click on the update manager and it says it needs to update it to the same version that installed. I tell it to update. It uses the downloaded package, and reinstalls.However the update manager still thinks it needs to be updated.

Minor issue but the update manager tray icon is bugging me.

---

### Post by zvacet on 2007-11-05
**synaptic<find vmware player>package>lock version**

Maybe this will help you.

---

### Post by emullet on 2007-11-06
Bash error when I run that command.

bash: find: No such file or directory

Copied and pasted it. Other ideas?

---

### Post by r4l on 2008-02-27
You can do this using the Synaptic Package Manger.

Go to System - Administration - Synaptic Package Manager to launch it, then search for vmware-player. It should like the package and show it as installed.

Under the Package menu, select the Lock Application.

I've had the same bug on my system.  If anyone knows why this is happening, would be cool to solve this one.

Thanks,

Doug.

---

### Post by r4l on 2008-02-27
Looks like that post was a little premature.  The version installed is locked, but the bug with the update manager persists.

---

### Post by robojiannis on 2008-02-29
As a temporary solution, I removed the repository after the install...

---

