---
title: "wicd: GPG error after upgrade - NO_PUBKEY"
date: 2008-09-30
forum: Installation &amp; Upgrades
---

### Post by serimp on 2008-09-30
I'm running 8.04 hardy with wicd; a few days ago the update manager caused the wicd upgrade to 1.5.3. The upgrade asked for the permission to overwrite some files, but in that moment I was too busy to annotate the file names :D

Now all work fine, but when I try 'apt-get update' I receive a GPG error saying that there is NO_PUBKEY FEC820F4B8C0755A. In /etc/apt/sources.list I have deb [http://apt.wicd.net](http://apt.wicd.net) hardy extras.

I also tried the command  gpg --keyserver subkeys.pgp.net --recv-keys FEC820F4B8C0755A, but the response was:

gpg: requesting key B8C0755A from hkp server subkeys.pgp.net
gpgkeys: key FEC820F4B8C0755A not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

Any help? Thanks in advance.
Sergio

---

### Post by serimp on 2008-09-30
I was able to find how to solve the problem by myself, and I annotate here what I have done, as it seems that there are many people looking for a solution,

Starting from the web page [http://apt.wicd.net/](http://apt.wicd.net/) click the link on the phrase 

'GPG signatures:The key used for signing is B8C0755A' 

on the right side of the page. A new page appears with the public key that is needed to validate the wicd apt source. Cut the content of the page and paste it in a file. It is necessary to cut and paste the full content of the page, including the starting line:

-----BEGIN PGP PUBLIC KEY BLOCK-----

and the ending line:

-----END PGP PUBLIC KEY BLOCK-----

Once the file is created, launch Synaptic package Manager, select the menu Setting/Repository, activate the tab Authentication and press the 'Import Key File' button. This let to select the file and import the public key. That's all! :D

Sergio

---

### Post by timking on 2008-09-30
Sergio,

Thank you - I was seeing the same problem.

---

### Post by serimp on 2008-10-01
Timking,
I am glad you solved after reading my post; however, in this forum other people suggest an easiest solution:

wget -q [http://apt.wicd.net/wicd.gpg](http://apt.wicd.net/wicd.gpg) -O- | sudo apt-key add -

Sergio

---

### Post by zvacet on 2008-10-01
[B]gpg --keyserver hkp://subkeys.pgp.net --recv-keys  FEC820F4B8C0755A
gpg --export --armor  FEC820F4B8C0755A | sudo apt-key add -[/B]

---

### Post by Chemist on 2008-10-03
Thanks guys, I was getting the same error

---

### Post by AJB2K3 on 2009-05-21
> **serimp said:**
> I was able to find how to solve the problem by myself, and I annotate here what I have done, as it seems that there are many people looking for a solution,

Starting from the web page [http://apt.wicd.net/](http://apt.wicd.net/) click the link on the phrase 

'GPG signatures:The key used for signing is B8C0755A' 

on the right side of the page. A new page appears with the public key that is needed to validate the wicd apt source. Cut the content of the page and paste it in a file. It is necessary to cut and paste the full content of the page, including the starting line:

-----BEGIN PGP PUBLIC KEY BLOCK-----

and the ending line:

-----END PGP PUBLIC KEY BLOCK-----

Once the file is created, launch Synaptic package Manager, select the menu Setting/Repository, activate the tab Authentication and press the 'Import Key File' button. This let to select the file and import the public key. That's all! :D

Sergio

Thanks solved it for me.

---

