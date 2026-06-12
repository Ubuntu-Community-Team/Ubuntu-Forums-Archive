---
title: "Can't upgrade to Feisty, got upd-man 0.45.4"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by Jonas_Henricsson on 2007-04-25
Ok, so I just installed Edgy and I've installed update-manager 0.45.4. Still I can't upgrade to Feisty. 

During the installation of Edgy something freaked out. The update-manager says the system is up-to-date first, so I click check. It then says that the following repository couldn't be found:
[http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz:](http://theli.free.fr/packages/dists/edgy/listen/binary-i386/Packages.gz:) 301 Moved Permanently

It then says:
W: GPG error: [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) edgy Release: Following signature could not be verified because public key is not available: NO_PUBKEY 2EBC26B60C5A2783

Then it does nothing. 

When I run synaptic it says the same.

What is causing this problem?

---

### Post by zvacet on 2007-04-25
Comment (put # sign in front of line) [http://theli.free.fr/packages/dists/...6/Packages.gz:](http://theli.free.fr/packages/dists/...6/Packages.gz:)

and for second  

[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
 gpg --export --armor KEY | sudo apt-key add -
[/B]

and for you it is

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783
 gpg --export --armor 2EBC26B60C5A2783  | sudo apt-key add -
 
```
sudo aptitude update
```

---

### Post by Jonas_Henricsson on 2007-04-25
That took care of the first error. 

I tried: 

gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783

I get back: 

gpg: demand key 0C5A2783 from hkp server subkeys.pgp.net
?: localhost: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused
gpg: found no valid OpenPGP-data.
gpg: Total number of processed units: 0

I tried: 

sudo gpg --keyserver hkp://subkeys.pgp.net --recv-keys 2EBC26B60C5A2783

It gives: 

gpg: WARNING: unsafe ownership of configuration file "/home/jonas/.gnupg/gpg.conf"
gpg: request by external program is inactivated because of unsecure authorities for set up file
gpg: communication error to key server: general error
gpg: download from key server failed: general error


Seems kind of messy, doesn't it?

---

