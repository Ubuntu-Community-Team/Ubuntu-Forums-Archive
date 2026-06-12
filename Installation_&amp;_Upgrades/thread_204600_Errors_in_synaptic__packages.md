---
title: "Errors in synaptic  packages"
date: 2006-06-27
forum: Installation &amp; Upgrades
---

### Post by bachiotomy on 2006-06-27
Hi, I'm very new to Linux. I've just made the switch from XP to ubuntu.. So far I'm pretty happy.Still trying to get everything configured.](*,) I was able to install a good amnount through synaptic packages. I'm having some problems with repositories... and have no idea how to use the terminal. But now I'm getting an error when i open synaptic package manager.

---

### Post by sparhawk on 2006-06-27
Your repository sources must have been changed by you or an app you installed. That is an unofficial repository and may no longer exist. That would be why you are getting the error. Its looking for the w32codecs which depending on what country you live in... may or may not be legal to download. If you wish to prevent the error just enter this in a terminal 

[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR]

and remove the repository giving you the trouble.

Let me know if you have any problems

---

### Post by bachiotomy on 2006-06-27
[QUOTE=sparhawk]Your repository sources must have been changed by you or an app you installed. That is an unofficial repository and may no longer exist. That would be why you are getting the error. Its looking for the w32codecs which depending on what country you live in... may or may not be legal to download. If you wish to prevent the error just enter this in a terminal 

[COLOR="Red"]sudo gedit /etc/apt/sources.list[/COLOR]

and remove the repository giving you the trouble.

Let me know if you have any problems[/QUOTE]
Great thanks for that help..:D I removed the line... and now I get this....

> W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_restricted_binary-i386_Packages)


Also:
> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5

then i get...
> W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060531)_dists_dapper_restricted_binary-i386_Packages)


---

### Post by bachiotomy on 2006-06-28
So much for discussing i guess I just have to go back to reading and screwing up my computer...

---

### Post by sparhawk on 2006-06-28
[QUOTE=bachiotomy]So much for discussing i guess I just have to go back to reading and screwing up my computer...[/QUOTE]

Post your sources list. I am at work now but when I get a chance I will post you mine so that you can see the official repositories and at least make sure they are in there.

---

### Post by sparhawk on 2006-06-28
Try going to this site to generate a new list for you system

[http://www.ubuntulinux.nl/source-o-matic](http://www.ubuntulinux.nl/source-o-matic)

That should help you get on the right path.

Remember the warning on the page about using the unsupported repositories.

---

