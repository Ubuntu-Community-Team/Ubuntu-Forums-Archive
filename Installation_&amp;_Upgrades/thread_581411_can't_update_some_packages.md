---
title: "can't update some packages"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by carlosjoan91 on 2007-10-19
hi, im tryin to update to 7.10, and i read that before that i need to have an up-to-date system, so i installed all uodates from the update manager, however when i oopen said manager it tells me that not all updates could be installed, and that i should do a partial dist upgrade but when i click the partial upgrade button it gives me an error that says that there was an error authenticating some packages, and the package list is:
dvdrip
ffmpeg
libavcodeccvs51
libavformatcvs51
libavutilcvs49
libfaad0
libgpod-common
libgpod1
libmjpegtools0
libpostproccvs51
libswscalecvs0
libx264-54
transcode

sdoes anyone have any idea why is this happening? would it be safe to update to 7.10 in this conditions? thanks in advance

edit: i dont know if this helps, but when i open update manager, before the  message that says i have to do a partial dist-upgrade, when i click the check for updates button it tels me
 W: GPG error: [http://ftp.eq.uc.pt](http://ftp.eq.uc.pt) stable Release: Las firmas siguientes no se pudieron verificar porque su llave pública no está disponible: NO_PUBKEY 07DC563D1F41B907

---

### Post by jrasmussen0 on 2007-10-19
It is safe to upgrade as long as you trust your source of packages.

The authentication error you get is all about not having the public signature file from [http://ftp.eq.uc.pt](http://ftp.eq.uc.pt) authorized to be trusted by apt (apt-key).  You can ignore the message if you trust your source of packages or you can add the key to the trusted list for apt with a apt-key add <file>.

For the upgrade, gutsy should disable any deb lines in /etc/apt/sources.list that are not from ubuntu.  Wait until after a successful upgrade before trying to install 3rd party packages from other repositories.

---

### Post by tonys_ub on 2007-11-22
Me too!        When I go into system up date i get a window that pops up and says: "not all up date can be installed" and it says "partial upgrade". So i hit partial upgrade, then i get a distribution upgrade window, it runs for a second, then i get "error authenticating some packages". What should i do?

---

### Post by osdesk on 2007-12-07
I'm got the same message when updating on another box.  Like jrasmussen0 said it should be fine as long as you trust the sources.  You can change that by right clicking on the update icon, choose "Preferences", type in your passwd, and select the sources you wish.  

When using the Add/Remove feature under "Applications", you should be careful about installing Third Party stuff.

[ATTACH]52542[/ATTACH]

---

