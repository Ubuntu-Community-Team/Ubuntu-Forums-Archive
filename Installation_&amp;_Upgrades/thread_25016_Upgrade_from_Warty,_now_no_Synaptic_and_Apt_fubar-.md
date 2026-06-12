---
title: "Upgrade from Warty, now no Synaptic and Apt fubar-ed"
date: 2005-04-09
forum: Installation &amp; Upgrades
---

### Post by maruchan on 2005-04-09
Just upgraded from Warty by going to synaptic's options and changing the word "Warty" to "Hoary", then Smart Mark-all and Apply. Well, it seemed to like that, except where I changed "Warty Backports" to "Hoary Backports". Didn't seem too critical, though.

Now, after a long install and rebooting it looks like everything went swell, except I can't find Synaptic anywhere and "apt-get update" throws this:

> Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports Release.gpg
Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports Release
Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Ign [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/universe Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release
Err [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages
  403 Forbidden
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Err [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/universe Packages
  403 Forbidden
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Get:3 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release.gpg [189B]
Get:4 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release.gpg [189B]
Get:5 [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release.gpg [189B]
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Ign [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable/main Packages
Hit [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages
Fetched 569B in 6s (92B/s)
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/hoary-backports/main/binary-i386/Packages.gz](http://ubuntu-bp.sourceforge.net/ubuntu/dists/hoary-backports/main/binary-i386/Packages.gz)  403 Forbidden
Failed to fetch [http://ubuntu-bp.sourceforge.net/ubuntu/dists/hoary-backports/universe/binary-i386/Packages.gz](http://ubuntu-bp.sourceforge.net/ubuntu/dists/hoary-backports/universe/binary-i386/Packages.gz)  403 Forbidden
Reading package lists... Done
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: GPG error: [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 07DC563D1F41B907
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-bp.sourceforge.net](http://ubuntu-bp.sourceforge.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-bp.sourceforge.net_ubuntu_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.


When I tried "apt-get synaptic", it told me this:

> E: Invalid operation synaptic

So I'm not sure what to do. I would like to have Synaptic running and the ability to install stuff nicely :)

Thanks for any help.

---

### Post by jono.carnie on 2005-04-09
Ok, lets start with an easy one.

The syntax is "sudo apt-get install synaptic"

Unless you've changed the sudo stuff so you nolonger need to use it.

As far as all the gpg stuff goes, take a look at this:
[http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary](http://www.ubuntulinux.org/wiki/AptAuthenticationInstructionsForHoary)

Get those two working first and then lets look at the missing stuff.

JC

---

### Post by maruchan on 2005-04-09
Forgot to mention I ran it in a root terminal, sorry :)

Actually I got it working last night/this morning early. I was so sleepy I don't remember everything I did, but I ran the scripts that I found in the HOWTO section, that I know for sure.

Anyway, APT and Synaptic both work now (there is no Synaptic icon in the menu bar though - just a plain one.).

Thanks for the help.

---

### Post by Leif on 2005-04-09
Please note that the backport reps have changed address :

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted

deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

---

### Post by maruchan on 2005-04-09
Cool, thanks for letting me know. I just changed them.

---

### Post by Bil-E-daKid on 2005-04-18
Hey guys,

Is there a GPG key for the backports too? I'm getting 'package could not be authenticated' errors when installing from the backports repositories (like the gimp updates that came through today).

Cheers
Bil

---

