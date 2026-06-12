---
title: "GPG problemos"
date: 2007-03-15
forum: Installation &amp; Upgrades
---

### Post by Ubukanuba on 2007-03-15
W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466

I get this every time I try to install a new program.  I just started using Ubuntu 6.10 and I cant get it to install everything!

I am also gettting this all the time trying to run install in automatix 2:

[03/14/2007 - 18:51.04] - ERRORS OR WARNINGS WHERE REPORTED
[03/14/2007 - 18:51.04] - FATAL - XChat - An apt-based error occured and installation was unsuccessful
[03/14/2007 - 20:03.59] - !!Starting Automatix 1.1-2.16!!
[03/14/2007 - 20:04.13] - !!SCRIPT OUTPUT START!!
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

W: GPG error: [http://mirror.ubuntulinux.nl](http://mirror.ubuntulinux.nl) edgy-seveas Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 49A120FD1135D466




THANK YOU!
-UBUKANUBA

---

### Post by Kateikyoushi on 2007-03-15
Run this in terminal, then try to update again.

```
gpg --keyserver subkeys.pgp.net --recv 49A120FD1135D466
gpg --export --armor 49A120FD1135D466 | sudo apt-key add -
```

---

### Post by Ubukanuba on 2007-03-15
RAN those and got:

OK

any ideas??

---

### Post by Ubukanuba on 2007-03-15
just tried to install moblock and got this.  I keep getting this error too??

E: Couldn't find package moblock-nfq

I am not sure but it doesnt seem to be connecting to all of the sites on my repositories.......nOoB to linux Thanks so Much!  

Free the internets from Willy G!Boycott Vista!

---

### Post by Kateikyoushi on 2007-03-15
Run this in terminal and post the output.
```
sudo aptitude update
```

---

### Post by Ubukanuba on 2007-03-15
> E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
E: Couldn't rebuild package cache
 

Gracias!

---

### Post by Kateikyoushi on 2007-03-15
Do you run anything else like synaptic or update manager ?

---

### Post by Ubukanuba on 2007-03-16
I have run update manager and got everything updated.  Synaptic I have some files downloaded but my main problem right now is I cant watch any DVD's in VLC media player or totem or any of the other media players.  Plus my dvdr drive is showing up as a cdrom drive??

---

### Post by Kateikyoushi on 2007-03-16
Then good, you got the previous error message because you used more than one application the same time which needs apt.
The DVD shos up in Nautilus as CDrom for me too, to play dvds you need codec to install it read this. [LINK]("https://help.ubuntu.com/community/RestrictedFormats")

---

