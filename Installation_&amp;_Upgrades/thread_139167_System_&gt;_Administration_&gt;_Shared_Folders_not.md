---
title: "System &gt; Administration &gt; Shared Folders not working"
date: 2006-03-03
forum: Installation &amp; Upgrades
---

### Post by iNerdSure on 2006-03-03
I'm trying to install a home LAN comprising:
   1 desktop (Win98), 
   1 latop (WinXP)
   1 laptop (Breezy5.10)

LAN functioning ok with WinXP, Win98 and printer that is connected to printer sharing port on router.

Have installed Samba using Synaptic Package Manager. However when I select folder to share using System > Administration > Shared Folders, the "Settings" menu window is "greyed" out, without any functionality for me to add "Shared folder/s"

Can some experts in the forum point me in the right direction, please. Thanks in advance.

---

### Post by iNerdSure on 2006-03-03
When i run: gksudo shares-admin, I get this error message:
> 
(gksudo:9305): Gdk-WARNING **: locale not supported by Xlib

(gksudo:9305): Gdk-WARNING **: cannot set locale modifiers

(shares-admin:9307): Gdk-WARNING **: locale not supported by Xlib

(shares-admin:9307): Gdk-WARNING **: cannot set locale modifiers

(shares-admin:9307): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
*** glibc detected *** double free or corruption (fasttop): 0x0825b0d0 ***

Can some experts in the community help? Many thanks.

---

### Post by LordBug on 2006-03-03
The question is:  Which system is the fileserver?

Samba itself is only needed if you want to setup shares on the Linux laptop.  I only have experience doing this via editting the /etc/samba/smb.conf file (though an easier way would be nice...)

If you're trying to get to shares on the Windows PCs from the Ubuntu machine, you can use mount (fs type smbfs), or the network viewer in Gnome.

---

### Post by iNerdSure on 2006-03-03
The intention is not to have a single PC or laptop as file-server. It is to have mutual access to shared folders on all the 3 systems. Previously, the LAN was set up with Win98, WinME and WinXP on each of the system. Now, it is on Win98, WinXP, and Breezy. The WinXP system is set up as dual boot with Breezy as well.

On the Breezy laptop, I can't even run "System > Adminsitration > Shared Folders" settings to select and designate a folder as "shared" to be accessible by the other 2 PCs.

Any idea what am I missing or doing incorrectly?

---

### Post by iNerdSure on 2006-03-05
Any expert out there in the community who can help with this "relatively" simple problem? Many thanks in advance.

---

