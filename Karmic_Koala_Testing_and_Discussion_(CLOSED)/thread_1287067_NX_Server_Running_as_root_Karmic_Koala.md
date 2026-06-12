---
title: "NX Server Running as root Karmic Koala"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Orbital_sFear on 2009-10-09
I recently installed Karmic Beta.  I'm  heavy Free-NX user.

When I got my new serverup and running, I attempted to shadow the X11 session and found that it was running as root.  I don't know why the change, since all other versions run as the user that is logged in.  I did however find a work around.

log into the server in question.

Edit: /usr/NX/etc/server.cfg

Change the line:
#EnableAdministratorLogin = "0"
to read:
EnableAdministratorLogin = "1"

Change the line:
#EnableAdministratorDesktopSharing = "0"
to read:
EnableAdministratorDesktopSharing = "1"

Change the line:
#EnableSystemDesktopSharingAuthorization = "1"
to read:
EnableSystemDesktopSharingAuthorization = "0"

Add the user root:
sudo /usr/NX/bin/nxserver --useradd root

The changes take affect immediately and you should now be able to shadow your display on Karmic.

---

### Post by bapoumba on 2009-10-10
Moved to Karmic.

---

